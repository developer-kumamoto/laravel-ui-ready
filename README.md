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
3. Open console.
4. Build image and Up services.
   ```command:title
   docker-compose build --no-cache
   docker-compose up -d
   ```
5. Create laravel project.
   ```command:title
   docker-compose exec app composer create-project laravel/laravel breeze-sample
   ```
   *Option: If windows....*
   ```command:title
   docker-compose exec app chmod guo+w -R breeze-sample/storage
   ```
6. Change 'root' and add 'index' in infra/nginx/default.conf.
   ```default.conf:title
   root /var/www/html/breeze-sample/public;
   index index.php;
   ```
7. Access localhost:8888 to confirm laravel available.
   ```command:title
   docker-compose restart web
   ```
8. Down services.
   ```command:title
   docker-compose down -v
   ```
9. Change 'app' work_dir from '/var/www/html' to '/var/www/html/breeze-sample' and start services.
   ```command:title
   docker-compose up -d
   ```
10. Change laravel .env file depend on 'db' service settings.
11. Migrate db.
    ```command:title
    docker-compose exec app php artisan migrate
    ```
12. Install laravel/breeze
    ```command:title
      docker-compose exec app composer require laravel/breeze --dev
      docker-compose exec app php artisan breeze:install
      docker-compose exec app npm install
      docker-compose exec app npm run dev
      docker-compose exec app php artisan migrate
    ```
13. Access localhost:8888 and Play breeze authentication.