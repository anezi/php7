PHP7 Binary for Ubuntu 14.04 64bits and compatibles OS.
=======================================================

Installation
------------

### Clone the repository

```bash
$ cd /usr/local/
$ git clone https://git.anezi.net/binary/php7-ubuntu-14.04-64 php7
```

### Copy pear configuration

```bash
$ cd /usr/local/php7/etc/pear.conf.default /etc/pear.conf
```

Update the repository binary
----------------------------

### Install compilation dependencies

```bash
$ sudo apt-get install bison libcurl4-openssl-dev
```

### Download and extract the files

```bash
$ cd /tmp

# Download the source
$ wget https://github.com/php/php-src/archive/php-7.0.0RC7.tar.gz

# Extract files.
$ tar -zxvf php-7.0.0RC7.tar.gz
```

### Compilation

```bash
$ cd php-7.0.0RC7

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

### Installation

```bash
# Installation
sudo make install
```