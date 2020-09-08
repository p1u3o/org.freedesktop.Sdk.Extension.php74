# org.freedesktop.Sdk.Extension.php8

This extension adds PHP support to Flatpak.

PHP installs to `/usr/lib/sdk/php8` inside the sandbox.

Example Visual Studio Code Configuration

```json
"php.validate.executablePath": "/usr/lib/sdk/php8/bin/php",
"php.executablePath": "/usr/lib/sdk/php8/bin/php",
```

Includes

* [php](https://php.net/) (8.0.0beta3)
* [composer](https://github.com/composer/composer) (1.10.10)
* [PHIVE](https://phar.io/) (0.14.4)
* [apcu](https://pecl.php.net/package/APCu) (5.1.18)
* [xdebug](https://xdebug.org/) (3.0.0-dev)

Each Flatpak can have its own custom php configuration files.
e.g. for Visual Studio Code
`~/.var/app/com.visualstudio.code/config/php/8.0/ini/my-custom.ini` or `/var/config/php/8.0/ini/my-custom.ini` from a sandboxed shell.

Global composer installs are limited to the Flatpak they were installed in.

#### Troubleshooting
`/usr/bin/env: ‘php’: No such file or directory`

Run `. /usr/lib/sdk/php8/enable.sh` or add `/usr/lib/sdk/php8/bin` to your $PATH.

#### Modules

```bash
bash-5.0$ php -m
[PHP Modules]
apcu
bcmath
bz2
calendar
Core
ctype
curl
date
dom
exif
FFI
fileinfo
filter
ftp
gd
gettext
hash
iconv
intl
json
ldap
libxml
mbstring
mysqli
mysqlnd
openssl
pcntl
pcre
PDO
pdo_mysql
pdo_pgsql
pdo_sqlite
Phar
posix
pspell
readline
Reflection
session
SimpleXML
sockets
sodium
SPL
sqlite3
standard
sysvmsg
sysvsem
sysvshm
tokenizer
xdebug
xml
xmlreader
xmlwriter
xsl
zip
zlib

[Zend Modules]
Xdebug
```
#### Build
```bash
flatpak-builder --repo repo .build org.freedesktop.Sdk.Extension.php8.json --force-clean
```
