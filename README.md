# LARAVEL SAIL | DOCKER COMPOSER

Documentation to follow of experiences setting up Dockerized PHP applications with Laravel.

NOTE: modifications were made to accomodate customized local serving of the application, as ports 80 and 3306 are not available for local development.

## Initial setup process

1. run `curl -s "https://laravel.build/example-app" | bash` to bootstrap the initial Laravel app
2. Change into project directory
3. Make modifications (detailed below) to `docker-compose.yml`
4. Make modifications (detailed below) to `vendor/laravel/sail/bin/sail`
5. Ensure Docker Desktop is running
6. Run `./vendor/bin/sail up` to start Docker
7. Application will be served on `localhost:8080`

## Modifications to `docker-compose.yml`

The following change on line 14:
```
ports:
  - '${APP_PORT:-80}:80'
```

... and the following change from line 31:
```
mysql:
    image: 'mysql/mysql-server:8.0'
    ports:
        - '${FORWARD_DB_PORT:-3307}:3306'
```

## Modifications to `sail`

A single change on line 126:
```export APP_PORT=${APP_PORT:-8080}```