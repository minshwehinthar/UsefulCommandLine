# 🔴 Laravel & PHP Artisan Quick Reference Guide

Essential command guide for building, managing, optimizing, and debugging Laravel applications using PHP Artisan.

---

## 📑 Table of Contents
- [Application & Server Operations](#-application--server-operations)
- [Database & Migrations](#-database--migrations)
- [Generator Commands (make)](#-generator-commands-make)
- [Optimization & Maintenance](#-optimization--maintenance)
- [Running Artisan via Docker](#-running-artisan-commands-via-docker)

---

## ⚡ Application & Server Operations

| Command | Description |
| :--- | :--- |
| `php artisan serve` | Start local development server |
| `php artisan tinker` | Run interactive PHP REPL shell |
| `php artisan route:list` | Display all registered application routes |
| `php artisan optimize:clear` | Clear all cached configuration, routes, and views |
| `php artisan key:generate` | Set application encryption key in `.env` |
| `php artisan storage:link` | Create symbolic link from `public/storage` to `storage/app/public` |

---

## 🗄️ Database & Migrations

| Command | Description |
| :--- | :--- |
| `php artisan migrate` | Execute all pending migrations |
| `php artisan migrate:status` | Show status of each migration |
| `php artisan migrate:rollback` | Roll back the last migration batch |
| `php artisan migrate:reset` | Roll back all application migrations |
| `php artisan migrate:refresh` | Reset and re-run all migrations |
| `php artisan migrate:fresh --seed` | Drop all tables, run migrations, and seed database |
| `php artisan db:seed` | Run default database seeders |
| `php artisan db:seed --class=UserSeeder` | Run a specific database seeder |
| `php artisan db:wipe` | Drop all database tables, views, and types |

---

## 🛠️ Generator Commands (`make`)

| Action | Command |
| :--- | :--- |
| **Model** | `php artisan make:model ModelName` |
| **Model with Migration** | `php artisan make:model ModelName -m` |
| **Model + Migration + Factory + Controller** | `php artisan make:model ModelName -mfc` |
| **Model with All Resources** | `php artisan make:model ModelName --all` |
| **Resource Controller** | `php artisan make:controller UserController --resource` |
| **API Controller** | `php artisan make:controller API/UserController --api` |
| **Form Request** | `php artisan make:request StoreUserRequest` |
| **Migration** | `php artisan make:migration create_orders_table` |
| **Seeder** | `php artisan make:seeder OrderSeeder` |
| **Factory** | `php artisan make:factory OrderFactory` |
| **Middleware** | `php artisan make:middleware CheckRole` |
| **Console Command** | `php artisan make:command SendEmails` |
| **Queue Job** | `php artisan make:job ProcessPayment` |
| **Event & Listener** | `php artisan make:event OrderShipped` / `php artisan make:listener SendInvoice` |

---

## 🧹 Optimization & Maintenance

```bash
# Cache configuration, routes, and views for production
php artisan config:cache
php artisan route:cache
php artisan view:cache
php artisan event:cache

# Put application into maintenance mode (with secret bypass)
php artisan down --secret="bypass-token-123"

# Bring application out of maintenance mode
php artisan up
```

---

## ⚙️ Running Artisan Commands via Docker

When running Laravel inside a Dockerized container environment:

```bash
# Using Docker Compose
docker compose exec app php artisan migrate

# Using Laravel Sail
./vendor/bin/sail artisan migrate
```