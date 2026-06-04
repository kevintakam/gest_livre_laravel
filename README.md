# Laravel 13 - Mini application de gestion de livres

## Objectif

Créer une mini-application Laravel permettant de gérer :

- inscription utilisateur
- connexion utilisateur
- ajout de livres
- affichage des livres
- modification des livres
- suppression des livres
- interface Blade
- Tailwind CSS
- MySQL

---

## Prérequis

```bash
php -v
composer -V
node -v
npm -v
mysql --version
```

---

## Création du projet

```bash
composer create-project laravel/laravel laravel-books
cd laravel-books
```

---

## Configuration MySQL

Dans `.env` :

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=db_books
DB_USERNAME=root
DB_PASSWORD=
```

---

## Authentification

```bash
composer require laravel/breeze --dev
php artisan breeze:install blade
npm install
npm run build
php artisan migrate
```

---

## Création du modèle Book

```bash
php artisan make:model Book -m
```

Migration :

```php
$table->id();
$table->string('title', 180);
$table->string('author', 120);
$table->string('isbn', 30)->nullable();
$table->text('description')->nullable();
$table->date('published_at')->nullable();
$table->boolean('available')->default(true);
$table->timestamps();
```

Puis :

```bash
php artisan migrate
```

---

## Contrôleur CRUD

```bash
php artisan make:controller BookController --resource --model=Book
```

---

## Validation

```bash
php artisan make:request StoreBookRequest
php artisan make:request UpdateBookRequest
```

---

## Routes protégées

```php
Route::middleware(['auth'])->group(function (): void {
    Route::resource('books', BookController::class);
});
```

---

## Compilation des assets

```bash
npm run dev
```

Production :

```bash
npm run build
```

---

## Workflow quotidien

```bash
composer install
npm install
php artisan migrate
npm run dev
php artisan serve
```

---

## Structure du projet

```text
laravel-books/
├── app/
├── bootstrap/
├── config/
├── database/
├── public/
├── resources/
├── routes/
├── storage/
├── tests/
├── .env
├── composer.json
├── package.json
└── vite.config.js
```

---

## Références

- https://laravel.com/docs/13.x/releases
- https://laravel.com/docs/13.x/starter-kits
- https://github.com/laravel/breeze
- https://tailwindcss.com/docs/guides/laravel
