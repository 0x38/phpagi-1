# phpagi
A modernized version of the original *phpagi* project
(http://phpagi.sourceforge.net/).

## Installation
To install, use composer:

```json
{
	"require": {
		"agiphlow/phpagi": "master-dev"
	}
}
```

## Sample script

The following script will reproduce the sound `welcome`,
usually included on a clean Asterisk installation
(see `/var/lib/asterisk/sounds` for more sounds).
Make sure the script file is executable.

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

To test it, you will need to add an extension to your
dialplan. Add the following to `/etc/asterisk/extensions.conf`:

```
exten => *111,1,agi(dtmf.php)
```

Now dial `*111` to test your script.
