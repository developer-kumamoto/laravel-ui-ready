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
   
