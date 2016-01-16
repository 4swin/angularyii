Simple quiz application using AngularJS and Yii

Requirements:
Yii 1.1.x
AngularJS 1.4.x

Prerequisites:
Pretty URL

<b>Pretty URL in Yii</b>
========================

1. Enable Apache's mod_rewrite
2. Add the following block in the default Apache configuration file:
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
3. Restart Apache
4. Add .htaccess file in your app's root directory, add this lines:
	RewriteEngine on

	# if a directory or a file exists, use it directly
	RewriteCond %{REQUEST_FILENAME} !-f
	RewriteCond %{REQUEST_FILENAME} !-d

	# otherwise forward it to index.php
	RewriteRule . index.php
5. Uncomment/add the urlManager components in app/protected/config/main.php
	'urlManager'=>array(
		'urlFormat'=>'path',
		'showScriptName'=>false,
		'rules'=>array(
			'<controller:\w+>/<id:\d+>'=>'<controller>/view',
			'<controller:\w+>/<action:\w+>/<id:\d+>'=>'<controller>/<action>',
			'<controller:\w+>/<action:\w+>'=>'<controller>/<action>',
		),
	),


<b>References</b>
=================

<a href="http://www.yiiframework.com/doc/guide/1.1/en/topics.url">URL Management</a>
<a href="https://www.digitalocean.com/community/tutorials/how-to-set-up-mod_rewrite-for-apache-on-ubuntu-14-04">Enabling mod_rewrite on Ubuntu 14.04</a>