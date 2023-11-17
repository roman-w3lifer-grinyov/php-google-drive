# php-google-drive

- [Installation](#installation)
- [Usage](#usage)

## Installation

``` sh
composer require w3lifer/php-google-drive
```

## Usage

``` php
<?php

require_once __DIR__ . '/vendor/autoload.php';

use w3lifer\google\PhpGoogleDrive;

$googleDrive = new PhpGoogleDrive([
    'pathToCredentials' => __DIR__ . '/credentials.json', // Required
    'pathToToken' => __DIR__ . '/token.json', // Required
]);

$fileId = $googleDrive->upload(
    __DIR__ . '/hello.txt',  // Required
    [ // Optional
        '<folder id>',
        '<folder id>',
    ]
);
```

- Folder ID: `https://drive.google.com/drive/folders/<folder-id>`
