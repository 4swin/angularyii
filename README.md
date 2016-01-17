# Simple quiz application using AngularJS and Yii

### Requirements
- Yii 1.1.x
- AngularJS 1.4.x

### Prerequisites
- Pretty URL
- REST API

### Pretty URL in Yii
1. Enable Apache's mod_rewrite
2. Add the following block in the default Apache configuration file:
  ```
  <VirtualHost *:80>
    ...
    <Directory /var/www/html>
      Options Indexes FollowSymLinks MultiViews
      AllowOverride All
      Order allow,deny
      allow from all
    </Directory>
    ...
  </VirtualHost>
  ```
3. Restart Apache's service
4. Create .htaccess file in your app's root directory then add these lines:
  ```
  RewriteEngine on

  # if a directory or a file exists, use it directly
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d

  # otherwise forward it to index.php
  RewriteRule . index.php
  ```
5. Uncomment/add the urlManager components in app/protected/config/main.php
  ```
  'urlManager'=>array(
    'urlFormat'=>'path',
    'showScriptName'=>false,
    'rules'=>array(
    '<controller:\w+>/<id:\d+>'=>'<controller>/view',
    '<controller:\w+>/<action:\w+>/<id:\d+>'=>'<controller>/<action>',
    '<controller:\w+>/<action:\w+>'=>'<controller>/<action>',
    ),
  ),
  ```
### REST API

### References
1. [Yii URL Management](http://www.yiiframework.com/doc/guide/1.1/en/topics.url)
2. [Enabling mod_rewrite on Ubuntu 14.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-mod_rewrite-for-apache-on-ubuntu-14-04)