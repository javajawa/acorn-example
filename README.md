Acorn - Example Project
=======================

This project is a learning skeleton for developing for the Acorn framework.
You can either use the instructions here to start your own repo with it's own
history, or clone this repo to get a head start!

Getting Started
---------------

There are a number of different ways to start using the Acorn framework.
We strongly recommend using the versioning tool Git to manage your new project,
as this will make keeping the framework up to date easier, and also make it
easier to keep your project backed up in its development stages.

This project was set up in the following way:

```
mkdir acron-example
cd acorn-example

git init

git submodule add http://github.com/javajawa/acorn.git

mkdir exmaple
touch exmaple/site.php
cat "<?php define('PROJECT_NAME', 'example'); require('acron/bootstrap.php');" >> index.php

git add acorn exmaple index.php
git commit -m "Initial Commit"
```

This sets up a new repo, adds the Acorn framework as a submodule, and creates
the base files for the project.

The file ```index.php``` acts as the entry point for the project.

Apache Configuration
--------------------

There are a number of ways of setting up this project to be part of your website.
In essence, all that needs to happen is that requests are passed to ```index.php```.

If you have access to Apache's Configuration, you can set up an Alias

```xml
<VirtualHost *:80>
	[Previous Content Here]

	Alias /exmaple /path/to/acorn-example/index.php
	AddHandler x-httpd-php /exmaple

	<Files /path/to/acorn-example/index.php>
		Allow from all
	</Files>
</VirtualHost>
```

If the FollowSymlinks directive is enabled, you can also perform a similar
operation directly on the file system

```
$ ln -s /path/to/acorn-example/index.php /var/www/exmaple.php
```

You can also have the project inside the document root (often ```/var/www```).
The require statement in ```index.php``` should be updated to
```php
	require('/path/to/acorn-example/acorn/bootstrap.php');
```

Site Configuration
------------------

The core file of your project it ```site.php```, which is found in the project
directory. This file will always be loaded, and is a great place to set up
Routes, which control what pages clients see, and also any site data which is
shared across all pages.

Updating Acorn
--------------

To update acorn, you have to fetch and merge the updates. This is, however,
mainly handled by git itself:
```
$ cd acorn
$ git pull
```

When you update the Acorn sub-module in this way, it registers in the parent
repo in the same way as a file change - so don't forget to add and commit!

More Information
----------------

For more information on how Acorn works, take a look at the Acorn wiki on
github.

