# laravel-ui-ready (Laravel/Breeze)
Mnimum settings for starting Laravel/Breeze on docker.
+ 3 services
   + app
      + PHP-FPM    
      + Composer
      + Node
   + web
      + Nginx
   + db
      + MySQL

# How to use
1. Checkout. 
2. Adjust folder name depends on your enviroment.  
   The folder name of laravel is 'backend'.  
   Rename it to any name using "Replace All" in your editor function.
3. Open console.
4. Build image and Up services.
   ```command:title
   docker-compose build --no-cache
   ```
5. Create laravel project.
   ```command:title
   docker-compose run --rm app composer create-project laravel/laravel backend
   ```
6. Change laravel .env file depend on 'db' service settings.
    ```.env:title
    DB_CONNECTION=mysql
    DB_HOST=db
    DB_PORT=3306
    DB_DATABASE=backend_db
    DB_USERNAME=backend_user
    DB_PASSWORD=backend_password
    ```
7. Up for migrate.
   ```command:title
   docker-compose down -v
   docker-compose up -d
   ```
8. Migrate db.  
   *Option: If windows....*
   ```command:title
   docker-compose exec app chmod guo+w -R backend/storage
   ```
    ```command:title
    docker-compose exec -w /var/www/html/backend/ app php artisan cache:clear
    docker-compose exec -w /var/www/html/backend/ app php artisan migrate
    ```
9. Install laravel/breeze
    ```command:title
   docker-compose exec -w /var/www/html/backend/ app composer require laravel/breeze --dev
   docker-compose exec -w /var/www/html/backend/ app php artisan breeze:install
   docker-compose exec -w /var/www/html/backend/ app npm install
   docker-compose exec -w /var/www/html/backend/ app php artisan migrate
    ```
10. Run Laravel.
    ```
    docker-compose exec -w /var/www/html/backend/ app npm run dev
    ```
11. Access localhost:8888 and Play breeze authentication.