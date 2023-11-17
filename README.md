# php-google-drive

- [Installation](#installation)
- [Usage](#usage)
- [How to get Google Drive API credentials](#how-to-get-google-drive-api-credentials)
  - [Create a new project](#create-a-new-project)
  - [Enable Google Drive API](#enable-google-drive-api)
  - [Create credentials](#create-credentials)
  - [Publish app](#publish-app)
- [How to get a token](#how-to-get-a-token)

## Installation

``` sh
composer require w3lifer/php-google-drive
```

## Usage

``` php
<?php

// require_once __DIR__ . '/vendor/autoload.php';

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

## How to get Google Drive API credentials

### Create a new project

---

- https://console.cloud.google.com

> ![](https://i.stack.imgur.com/D0orV.png)

> ![](https://i.stack.imgur.com/dtqvu.png)

---

### Enable Google Drive API

---

> ![](https://i.stack.imgur.com/5S44Q.png)

> ![](https://i.stack.imgur.com/QEP5e.png)

> ![](https://i.stack.imgur.com/70YlU.png)

> ![](https://i.stack.imgur.com/Gz3gQ.png)

---

### Create credentials

---

> ![](https://i.stack.imgur.com/l9zBr.png)

<ins>If you left the screen above, go to "Enable API & services" and click "Google Drive API":</ins>

> ![](https://i.stack.imgur.com/jIjyu.png)

> ![](https://i.stack.imgur.com/BymkG.png)

> ![](https://i.stack.imgur.com/wkBrU.png)

> ![](https://i.stack.imgur.com/vBdC1.png)

> ![](https://i.stack.imgur.com/qXN5E.png)

> ![](https://i.stack.imgur.com/olM22.png)

---

### Publish app

---

> ![](https://i.stack.imgur.com/2txzO.png)

## How to get a token

**1. Save the credential to disk and specify the path to them by setting the `pathToCredentials` configuration key**

``` php
$googleDrive = new PhpGoogleDrive([
    'pathToCredentials' => __DIR__ . '/credentials.json', // Required
    'pathToToken' => __DIR__ . '/token.json', // Required
]);
```

> **Note** that `pathToToken` is the path where the `PhpGoogleDrive` saves the token after the first run. That is, the token will be saved automatically along the specified path; it is needed for your application to subsequently access Google Drive without the consent screen.

---

**2. Run your app**

- You will receive the following message in the console:

```
Open the following link in your browser:
https://accounts.google.com/o/oauth2/v2/auth?...
Enter verification code:
```

- Open the link in the message and choose desired account:

![](https://i.stack.imgur.com/lOzkM.png)

- The warning "Google hasn't verified this app" may appear. Click "Advanced" and then "Go to ... (unsafe)":

![](https://i.stack.imgur.com/YACgh.png)

- On the next screen click "Continue":

![](https://i.stack.imgur.com/wzWfm.png)

- After the redirect, copy the code from the address bar of your browser and paste it in the console:

![](https://i.stack.imgur.com/ZP45S.png)

```
Open the following link in your browser:
https://accounts.google.com/o/oauth2/v2/auth?...
Enter verification code: <here>
```

**3. Enjoy!**
