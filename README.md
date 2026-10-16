# Laravel Docker Setup

A Laravel application running in Docker using Docker Compose, Nginx, PHP-FPM, and MySQL.

This project was built while learning Docker and containerizing a Laravel application.

## Technologies Used

- Docker
- Docker Compose
- PHP 8.4
- Laravel 13
- Nginx
- MySQL
- Composer

## Project Structure

```text
laravel-demo/
├── docker-compose.yaml
├── dockerfiles/
│   ├── composer.dockerfile
│   ├── nginx.dockerfile
│   └── php.dockerfile
├── env/
│   └── mysql.env
├── nginx/
│   └── nginx.conf
└── src/
    ├── app/
    ├── bootstrap/
    ├── config/
    ├── database/
    ├── public/
    ├── resources/
    ├── routes/
    ├── storage/
    ├── composer.json
    └── artisan
```

## Features

- Runs Laravel inside Docker containers.
- Uses Nginx as the web server.
- Uses PHP-FPM to process PHP requests.
- Configures a MySQL database service.
- Uses Docker volumes to share application files with containers.
- Supports Laravel database migrations.
- Separates application services using Docker Compose.

## Prerequisites

Install the following before running the project:

- Docker Desktop
- Git

Docker Desktop should be running before you execute the commands below.

## Setup and Installation

### 1. Clone the repository

```bash
git clone https://github.com/SwatiManjari/laravel.git
cd laravel
```

### 2. Configure environment files

Create the Laravel environment file from the example:

```bash
cp src/.env.example src/.env
```

Configure the database settings in `src/.env` to match your MySQL service:

```env
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=homestead
DB_USERNAME=your_mysql_username
DB_PASSWORD=your_mysql_password
```

Replace the example username and password with the values configured in your local `env/mysql.env` file.

Create `env/mysql.env` locally and configure the MySQL container credentials according to `docker-compose.yaml`.

Do not commit environment files containing passwords or other secrets.

### 3. Start the containers

Build the required images and start the services:

```bash
docker-compose up -d --build
```

### 4. Generate the application key

```bash
docker-compose run --rm artisan key:generate
```

### 5. Run database migrations

```bash
docker-compose run --rm artisan migrate
```

### 6. Open the application

Visit the following address in your browser:

http://localhost:8000

## Useful Docker Commands

Start the services:

```bash
docker-compose up -d
```

Stop the services:

```bash
docker-compose down
```

Rebuild images and start the services:

```bash
docker-compose up -d --build
```

View running containers:

```bash
docker-compose ps
```

View container logs:

```bash
docker-compose logs
```

Clear Laravel's compiled Blade views:

```bash
docker-compose exec php php artisan view:clear
```

Run database migrations:

```bash
docker-compose run --rm artisan migrate
```

## What I Learned

- Building and running Docker images.
- Managing multiple services with Docker Compose.
- Connecting Nginx with PHP-FPM.
- Using bind mounts to share files between the host and containers.
- Configuring Laravel and MySQL for a containerized environment.
- Running Laravel Artisan commands inside containers.
- Managing file permissions for Laravel's writable directories.
- Debugging container and application errors.
- Using Git and GitHub to version-control a project.

## Author

Swati Manjari

GitHub: [SwatiManjari](https://github.com/SwatiManjari)
