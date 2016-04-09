# phpagi
A modernized version of the original *phpagi* project
(http://phpagi.sourceforge.net/).

## Installation

The suggested installation method is via [composer](https://getcomposer.org/):

```sh
composer require agiphlow/phpagi
```

** Note: ** `agiphlow/phpagi` is still in development, make sure to set
the minimum stability in your `composer.json` to `dev`:
```json
{
	...
	"minimum-stability": "dev"
	...
}
```

## Usage

Create the script `agi.php` with the following content:

```php
#!/usr/bin/env php
<?php

require_once __DIR__ .'vendor/autoload.php';

use Agiphlow\PhpAgi\Agi;

// create agi client
$agi = new Agi();

// answer the call
$agi->answer();

// play file
$agi->stream_file('welcome');

// hangup call
$agi->hangup();
```

Make sure the script is executable:

```
chmod a+x agi.php
```

To test it, you will need to add an extension to your
dialplan. Add the following to `/etc/asterisk/extensions.conf`:

```
exten => *111,1,agi(dtmf.php)
```

Now dial `*111` to test your script.
