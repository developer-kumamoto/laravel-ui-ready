# laravel-ui-ready
Mnimum settings for Laravel Breeze on docker.
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
6. Play as you like. e.g. Into app service and composer new sample-app, composer require laravel/breeze --dev
