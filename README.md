# Deploy Laravel on Vercel

## 😎 Getting Started

Let's picture you want to deploy your awesome microproject written in PHP and you don't know where. You have found [Vercel](https://vercel.com) it's awesome, but for static sites. Not anymore! I would like to introduce you your new best friend `vercel-php`, PHP runtime for Vercel platform.

Most simple example project is this one, using following project structure.

```sh
project
├── api
│   └── index.php
└── .vercelignore
└── vercel.json
```

First file `api/index.php` is entrypoint of our application. It should be placed in **api** folder, it's very standard location for Vercel.

```php
<?php
phpinfo();
```

Second file `vercel.json` is pure gold here. Setup your project with configuration like this and voila. That's all.

```json
{
    "functions": {
        "api/*.php": {
            "runtime": "vercel-php@0.6.0"
        }
    }
}
```

Last thing you have to do is call `vercel`. If you are more interested take a look at features and usage.

```
# Install it globally
npm i -g vercel

# Log in
vercel login

# Let's fly
vercel
```

Are you ready to deploy your first PHP project to Vercel? Click & Go!

<a href="https://vercel.com/new/project?template=https://github.com/juicyfx/vercel-examples/tree/master/php"><img src="https://vercel.com/button"></a>

## 🤗 Features

-   **Architecture**: PHP development server (🚀 fast enough)
-   **PHP version**: 8.2 (https://example-php-8-2.vercel.app)
-   **Extensions**: apcu, bcmath, brotli, bz2, calendar, Core, ctype, curl, date, dom, ds, exif, fileinfo, filter, ftp, geoip, gettext, hash, iconv, igbinary, imap, intl, json, libxml, lua, mbstring, mongodb, msgpack, mysqli, mysqlnd, openssl, pcntl, pcre, PDO, pdo_mysql, pdo_pgsql, pdo_sqlite, pgsql, phalcon, Phar, protobuf, readline, redis, Reflection, runkit7, session, SimpleXML, soap, sockets, sodium, SPL, sqlite3, standard, swoole, timecop, tokenizer, uuid, xml, xmlreader, xmlrpc, xmlwriter, xsl, Zend OPcache, zlib, zip
-   **Speed**: cold ~250ms / warm ~5ms
-   **Memory**: ~90mb
-   **Frameworks**: Nette, Symfony, Lumen, Slim, Phalcon

> List of all installable extensions is on this page https://blog.remirepo.net/pages/PECL-extensions-RPM-status.

## 💯 Versions

-   `vercel-php@0.6.0` - PHP 8.2.x (https://example-php-8-2.vercel.app)
-   `vercel-php@0.5.3` - PHP 8.1.x (https://example-php-8-1.vercel.app)
-   `vercel-php@0.4.1` - PHP 8.0.x (https://example-php-8-0.vercel.app)
-   `vercel-php@0.3.3` - PHP 7.4.x (https://example-php-7-4.vercel.app)

## ⚙️ Usage

Before you can start using this runtime, you should learn about Vercel and [how runtimes](https://vercel.com/docs/runtimes?query=runtime#official-runtimes) works. Take a look at blogpost about [`Serverless Functions`](https://vercel.com/blog/customizing-serverless-functions).

You should define `functions` property in `vercel.json` and list PHP files directly or using wildcard (\*).
If you need to route everything to index, use `routes` property.

```json
{
    "functions": {
        "api/*.php": {
            "runtime": "vercel-php@0.6.0"
        }
    },
    "routes": [{ "src": "/(.*)", "dest": "/api/index.php" }]
}
```

Do you have more questions (❓)? Let's move to [FAQ](#%EF%B8%8F-faq).

## 👨‍💻 `vercel dev`

For running `vercel dev` properly, you need to have PHP installed on your computer, [learn more](errors/now-dev-no-local-php.md).
But it's PHP and as you know PHP has built-in development server. It works out of box.
