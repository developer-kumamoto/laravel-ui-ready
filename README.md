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
4. Type "docker-compose build --no-cache"
5. Type "docker-compose up -d"
6. Create laravel project.
   ```command:title
      docker-compose run app composer create-project laravel/laravel breeze-sample
   ```
7. Change 'root' and add 'index' in infra/nginx/default.conf.
   ```default.conf:title
      root /var/www/html/breeze-sample/public;
      index index.php;
   ```
8. Type "docker-compose restart web"
9. Access localhost:8888 to confirm laravel available.
10. Type "docker-compose down"
11. Change 'app' work_dir from '/var/www/html' to '/var/www/html/breeze-sample'
12. Change laravel .env file depend on 'db' service settings.
13. Type "docker-compose up -d"
14. Install laravel/breeze
   ```command:title
      docker-compose run app php artisan migrate
      docker-compose run app composer require laravel/breeze --dev
      docker-compose run app php artisan breeze:install
      docker-compose run app npm install
      docker-compose run app npm run dev
      docker-compose run app php artisan migrate
   ```
15. Access localhost:8888 and Play breeze authentication.