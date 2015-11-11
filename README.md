PHP7 Binary for Ubuntu 14.04 64bits and compatibles OS.
=======================================================

1. Installation: Simple install of pre compiled PHP7 binary (Compiled in Ubuntu 12.04 64-bits)
2. Compilation from sources: Instructions to compile and install PHP7 from sources.

1. Installation
---------------

### 1.1 Install the dependencies

```bash
$ apt-get install libmcrypt4
```

### 1.2 Clone the repository

```bash
$ cd /usr/local/
$ git clone https://github.com/anezi/php7.git php7
```

### 1.3 Copy pear configuration

```bash
$ cp /usr/local/php7/etc/pear.conf.default /etc/pear.conf
$ cp /usr/local/php7/etc/php-fpm.conf.default /usr/local/php7/etc/php-fpm.conf
$ cp /usr/local/php7/etc/php-fpm.d/www.conf.default /usr/local/php7/etc/php-fpm.d/www.conf
```

### 1.4 Configuration of PHP7-FPM

```bash
$ cp /usr/local/php7/etc/init.d/php7-fpm.default /etc/init.d/php7-fpm
$ cp /usr/local/php7/etc/php-fpm.conf.default /usr/local/php7/etc/php-fpm.conf
```

2. Compilation from sources
---------------------------

### 2.1 Install compilation dependencies

```bash
$ sudo apt-get install bison libcurl4-openssl-dev
```

### 2.2 Download and extract the files

```bash
$ cd /tmp

# Download the source
$ wget https://github.com/php/php-src/archive/php-7.0.0RC7.tar.gz

# Extract files.
$ tar -zxvf php-7.0.0RC7.tar.gz
```

### 2.3 Compilation

```bash
$ cd php-src-php-7.0.0RC7

# Build configuration
./buildconf --force

# Prepare configuration
./configure --enable-fpm --prefix=/usr/local/php7 --enable-opcache --enable-intl --enable-mbstring --enable-zip \
        --enable-bcmath --enable-pcntl --enable-ftp --enable-exif --enable-calendar --enable-sysvmsg --enable-sysvsem \
        --enable-sysvshm --enable-wddx --enable-gd-native-ttf --enable-gd-jis-conv \
        --with-curl --with-mcrypt --with-iconv --with-gd --with-jpeg-dir=/usr --with-png-dir=/usr --with-zlib-dir=/usr \
        --with-freetype-dir=/usr --with-openssl --with-pdo-mysql=/usr --with-gettext=/usr --with-zlib=/usr --with-bz2=/usr \
        --with-mysqli=/usr/bin/mysql_config

# Compilation
make

# Run tests
make test
```

### 2.4 Installation

```bash
# Installation
sudo make install
```
