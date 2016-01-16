<h1>Simple quiz application using AngularJS and Yii</h1>

<h3>Requirements</h3>
<ul>
	<li>Yii 1.1.x</li>
	<li>AngularJS 1.4.x</li>
</ul>

<h3>Prerequisites</h3>
<ul>
	<li>Pretty URL</li>
</ul>

<h3>Pretty URL in Yii</h3>
<ol>
	<li>Enable Apache's mod_rewrite
	<li>
	Add the following block in the default Apache configuration file:</br>
	<pre>
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
	</pre>
	</li>
	<li>Restart Apache</li>
	<li>
	Add .htaccess file in your app's root directory, add this lines:<br>
	RewriteEngine on

	# if a directory or a file exists, use it directly
	RewriteCond %{REQUEST_FILENAME} !-f
	RewriteCond %{REQUEST_FILENAME} !-d

	# otherwise forward it to index.php
	RewriteRule . index.php
	</li>
	<li>
	Uncomment/add the urlManager components in app/protected/config/main.php<br>
	'urlManager'=>array(
		'urlFormat'=>'path',
		'showScriptName'=>false,
		'rules'=>array(
			'<controller:\w+>/<id:\d+>'=>'<controller>/view',
			'<controller:\w+>/<action:\w+>/<id:\d+>'=>'<controller>/<action>',
			'<controller:\w+>/<action:\w+>'=>'<controller>/<action>',
		),
	),
	</li>
</ol>

<h3>References</h3>
<ol>
<li><a href="http://www.yiiframework.com/doc/guide/1.1/en/topics.url">URL Management</a></li>
<li><a href="https://www.digitalocean.com/community/tutorials/how-to-set-up-mod_rewrite-for-apache-on-ubuntu-14-04">Enabling mod_rewrite on Ubuntu 14.04</a></li>
</ol>