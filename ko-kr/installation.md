---
layout: default
language: 'ko-kr'
version: '4.0'
title: '설치하기'
keywords: '설치, Phalcon 설치, 팔콘설치'
---

# 설치하기

* * *

![](/assets/images/document-status-stable-success.svg) ![](/assets/images/version-{{ page.version }}.svg)

## 사전 요구사항

### PHP 7.2

Phalcon v4는 PHP 7.2 이상만 지원합니다. PHP 7.1이 출시된 지 2년이 지났고 [기술지원(active support)](https://secure.php.net/supported-versions.php) 도 이제는 끝난 상황이라, 기술지원이 되는 PHP버전을 따르기로 결정했습니다.

### PSR

Phalcon은 PSR 익스텐션이 필요합니다. 이 익스텐션은 [여기](https://github.com/jbboehr/php-psr) 깃헙 저장소에서 다운로드 받아서 컴파일 할 수 있습니다. 설치 설명서는 저장소의 `README`에서 확인하실 수 있습니다. 익스텐션이 컴파일 되어 시스템에서 사용가능해 지면, `php.ini` 파일에 추가해 주어야 합니다. 다음과 같이 추가해 주시면 됩니다:

```ini
extension=psr.so
```

phalcon 익스텐션보다 위에 위치해야 함

```ini
extension=phalcon.so
```

일부 배포판의 경우 `ini` 파일명에 접두어로 숫자를 붙이는 경우가 있습니다. 그런 경우, Phalcon 에는 높은 숫자를 할당해 주세요 ( 예. `50-phalcon.ini`).

### PDO

Phalcon은 느슨하게 연결되어 있기 때문에, 추가적인 익스텐션 필요없이 기능을 사용할 수 있습니다. 하지만 특정 컴포넌트는 동작을 위해 추가적인 익스텐션이 필요한 경우가 있습니다. 데이터베이스 연결 및 사용이 필요한 경우, `php_pdo` 익스텐션을 설치해야 합니다. 사용중인 RDBMS가 MYSQL/MariaDB 혹은 Aurora인 경우, `php_mysqlnd` 익스텍션도 필요합니다. 마찬가지로, Phalcon에서 PostgreSql을 사용하는 경우 `php_pgsql` 익스텐션이 필요합니다.

### 하드웨어

Phalcon은 최고의 성능을 제공하면서도 가능한 최소의 리소스를 사용하도록 설계되어 있습니다. Phalcon을 다양한 저사양의 환경(예를 들어 0.5CPU에 0.25GB 램) 에서 테스트 해보기는 했지만, 하드웨어의 선택은 전적으로 구동시키는 어플리케이션의 필요에 따라야 할 것입니다.

우리는 최근 몇년간 아마존AWS에서 1 vCPU/512MB RAM 의 VM 사양으로 웹사이트와 블로그를 호스팅 해왔습니다.

### 소프트웨어

> **주의**: 버그 해결, 보안 강화 뿐만이 아니라 성능향상을 위해서라도 Phalcon과 PHP는 가능한 항상 최신버전을 사용해야 합니다.
{: .alert .alert-danger }

어플리케이션의 요구사항과 필요한 Phalcon 컴포넌트에 따라, PHP 7.2 이상을 사용해야 하는 것 외에도 다음의 익스텐션들을 추가해야 할 수 있습니다.

* [curl](https://secure.php.net/manual/en/book.curl.php)
* [fileinfo](https://secure.php.net/manual/en/book.fileinfo.php)
* [gettext](https://secure.php.net/manual/en/book.gettext.php)
* [gd2](https://secure.php.net/manual/en/book.image.php) ( [Phalcon\Image\Adapter\Gd](api/Phalcon_Image_Adapter_Gd) 클래스 사용시 필요)
* [imagick](https://secure.php.net/manual/en/book.imagick.php) ( [Phalcon\Image\Adapter\Imagick](api/Phalcon_Image_Adapter_Imagick) 클래스 사용시 필요)
* [json](https://secure.php.net/manual/en/book.json.php)
* `libpcre3-dev` (Debian/Ubuntu), `pcre-devel` (CentOS), `pcre` (macOS)
* [PDO](https://php.net/manual/en/book.pdo.php) 익스텐션과 사용해야할 특정 RDBMS 익스텐션 (즉, [MySQL](https://php.net/manual/en/ref.pdo-mysql.php), [PostgreSql](https://php.net/manual/en/ref.pdo-pgsql.php) 등)
* [OpenSSL](https://php.net/manual/en/book.openssl.php) 익스텐션
* [Mbstring](https://php.net/manual/en/book.mbstring.php) 익스텐션
* 캐시 사용 여부 및 방식에 따라 [Memcached](https://php.net/manual/en/book.memcached.php) 혹은 관련된 다른 캐시 어댑터

> **주의**: 이 패키지들의 설치는 사용중인 운영체제와 (있다면) 패키지관리자에 따라 달라질 수 있습니다. 이 익스텐션들의 설치방법에 대해서는 관련문서를 참조 해주세요.
{: .alert .alert-info }

`libpcre3-dev` 패키지의 경우에 다음의 명령어를 사용하시면 됩니다:

#### Debian

```bash
sudo apt-get install libpcre3-dev
```

설치 후 Phalcon을 다시한번 설치해주세요.

#### CentOS

```bash
sudo yum install pcre-devel
```

#### Mac/Osx using Brew

```bash
brew install pcre
```

Without `brew`, you need to go to the [PCRE](https://www.pcre.org/) website and download the latest pcre:

```bash
tar -xzvf pcre-8.42.tar.gz
cd pcre-8.42
./configure --prefix=/usr/local/pcre-8.42
make
make install
ln -s /usr/local/pcre-8.42 /usr/sbin/pcre
ln -s /usr/local/pcre-8.42/include/pcre.h /usr/include/pcre.h
```

For Maverick

```bash
brew install pcre
```

if it gives you error, you can use

```bash
sudo ln -s /opt/local/include/pcre.h /usr/include/
sudo pecl install apc 
```

## 설치 플랫폼

Since Phalcon is compiled as a PHP extension, its installation is somewhat different than any other traditional PHP framework. Phalcon needs to be installed and loaded as a module on your web server.

### Linux

To install Phalcon on Linux, you will need to add our repository in your distribution and then install it.

#### DEB Based Distributions (Debian, Ubuntu, Etc.)

##### 저장소 설치

Add the repository to your distribution:

**Stable releases**

```bash
curl -s https://packagecloud.io/install/repositories/phalcon/stable/script.deb.sh | sudo bash
```

**Nightly releases**

```bash
curl -s https://packagecloud.io/install/repositories/phalcon/nightly/script.deb.sh | sudo bash
```

**Mainline releases (alpha, beta etc.)**

```bash
curl -s https://packagecloud.io/install/repositories/phalcon/mainline/script.deb.sh | sudo bash
```

> **주의**: 이 버전의 경우에는 배포판을 변경하거나 Stable 릴리즈에서 nightly 빌드로 전환 하는 경우가 아니라면 최초 한번만 실행하시면 됩니다.
{: .alert .alert-warning }

##### Phalcon 설치

To install Phalcon you need to type the following commands in your terminal:

```bash
sudo apt-get update
sudo apt-get install php7.2-phalcon
```

##### 다른 PPA

**Ondřej Surý**

If you do not wish to use our repository at [packagecloud.io](https://packagecloud.io/phalcon), you can always use the one offered by [Ondřej Surý](https://launchpad.net/~ondrej/+archive/ubuntu/php/).

Installation of the repo:

```php
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
```

and Phalcon:

```php
sudo apt-get install php-phalcon
```

#### RPM Based Distributions (CentOS, Fedora, Etc.)

##### 저장소 설치

Add the repository to your distribution:

**Stable releases**

```bash
curl -s https://packagecloud.io/install/repositories/phalcon/stable/script.rpm.sh | sudo bash
```

**Nightly releases**

```bash
curl -s https://packagecloud.io/install/repositories/phalcon/nightly/script.rpm.sh | sudo bash
```

**Mainline releases (alpha, beta etc.)**

```bash
curl -s https://packagecloud.io/install/repositories/phalcon/mainline/script.rpm.sh | sudo bash
```

> **주의**: 이 버전의 경우에는 배포판을 변경하거나 Stable 릴리즈에서 nightly 빌드로 전환 하는 경우가 아니라면 최초 한번만 실행하시면 됩니다.
{: .alert .alert-warning }


##### Phalcon 설치

To install Phalcon you need to issue the following commands in your terminal:

```bash
sudo yum update
sudo yum install php72u-phalcon
```

##### 다른 RPM

**Remi**

[Remi Collet](https://github.com/remicollet) maintains an excellent repository for RPM based installations. You can find instructions on how to enable it for your distribution [here](https://blog.remirepo.net/pages/Config-en).

Installing Phalcon after that is as easy as:

```bash
yum install php72-php-phalcon4
```

Additional versions are available both architecture specific (x86/x64) as well as PHP version specific

#### FreeBSD

A port is available for FreeBSD. To install it you will need to issue the following commands:

##### pkg_add

```bash
pkg_add -r phalcon4
```

##### 소스

```bash
cd /usr/ports/www/phalcon4

make install clean
```

##### Gentoo

An overlay for installing Phalcon can be found [here](https://github.com/smoke/phalcon-gentoo-overlay)

#### Raspberry Pi

```bash
sudo -s
git clone https://github.com/phalcon/cphalcon
cd cphalcon/
git checkout tags/v4.0.0 ./
zephir fullclean
zephir build
```

It is also necessary to increase the swap file from the default 100 MB to at least 2000 MB. Because, the compiler lacks RAM.

```bash
sudo -s
nano /etc/dphys-swapfile
```

Replacing `CONF_SWAPSIZE=100` with `CONF_SWAPSIZE=2000`

After saving the setting, restart the daemon:

```bash
/etc/init.d/dphys-swapfile stop
/etc/init.d/dphys-swapfile start
```

### macOS

Brew includes binary packages so you don't need to compile Phalcon yourself. If you want to compile the extension yourself you need the following dependencies installed:

#### Compilation requirements

* PHP 7.x development resources
* XCode

#### Brew

Binary installation (preferred):

```bash
brew tap phalcon/extension https://github.com/phalcon/homebrew-tap
brew install phalcon
```

Compile phalcon:

```bash
brew tap phalcon/extension https://github.com/phalcon/homebrew-tap
brew install phalcon --build-from-source 
```

#### MacPorts

```bash
sudo port install php72-phalcon
sudo port install php73-phalcon
```

Edit your php.ini file and then append at the end:

```ini
extension=php_phalcon.so
```

Restart your webserver.

### Windows

To use Phalcon on Windows, you will need to install the phalcon.dll. We have compiled several DLLs depending on the target platform. The DLLs can be found in our [download](https://phalcon.io/en/download/windows) page.

Identify your PHP installation as well as architecture. If you download the wrong DLL, Phalcon will not work. `phpinfo()` contains this information. In the example below, we will need the NTS version of the DLL:

![phpinfo](/assets/images/content/phpinfo-api.png)

The available DLLs are:

| 아키텍처 | 버전  | 타입            |
|:----:|:---:| ------------- |
| x64  | 7.x | 멀티스레드 빌드(TS)  |
| x64  | 7.x | 단일스레드 빌드(NTS) |
| x86  | 7.x | 멀티스레드 빌드(TS)  |
| x86  | 7.x | 단일스레드 빌드(NTS) |

Edit your php.ini file and then append at the end:

```ini
extension=php_phalcon.dll
```

Restart your webserver.

### 소스를 직접 컴파일하기

Compiling from source is similar to most environments (Linux/macOS).

#### Requirements

* PHP 7.2x/7.3.x 개발 환경
* GCC 컴파일러 (리눅스/Solaris/FreeBSD) 혹은 Xcode (macOS)
* re2c >= 0.13
* libpcre-dev

#### Compilation

Download the latest `zephir.phar` from [here](https://github.com/phalcon/zephir/releases). Add it to a folder that can be accessed by your system.

Clone the repository

```bash
https://github.com/phalcon/cphalcon 저장소 복제
```

Compile Phalcon

```bash
cd cphalcon/
git checkout tags/v4.0.0 ./
zephir fullclean
zephir build
```

Check the module

```bash
php -m | grep phalcon
```

You will now need to add `extension=phalcon.so` to your PHP ini and restart your web server, so as to load the extension.

```ini
# Suse: Phalcon.ini 파일을 만들어 extension= phalcon.so 라인을 추가한 후 /etc/php7/conf.d/ 폴더에 저장해 주세요.

# CentOS/RedHat/Fedora: Phalcon.ini 파일을 만들어 extension=phalcon.so 라인을 추가한 후 /etc/php.d/ 폴더에 저장해 주세요.

# Ubuntu/Debian 에서 Apache2 사용시: 30-phalcon.ini 파일을 만들어 extension=phalcon.so 라인을 추가한 후 /etc/php7/apache2/conf.d/ 폴더에 저장해 주세요.

# Ubuntu/Debian 에서 Php7-fpm 사용시: 30-phalcon.ini 파일을 만들어 extension=phalcon.so 라인을 추가한 후 /etc/php7/fpm/conf.d/ 폴더에 저장해 주세요.

# Ubuntu/Debian 에서 Php7-cli 사용시: 30-phalcon.ini 파일을 만들어 extension=phalcon.so 라인을 추가한 후 /etc/php7/cli/conf.d/ 폴더에 저장해 주세요.
```

The instructions above will compile **and** install the module on your system. You can also compile the extension and then add it manually in your `ini` file:

```bash
cd cphalcon/
git checkout tags/v4.0.0 ./
zephir fullclean
zephir compile
cd ext
phpize
./configure
make && make install
```

If you use the above method you will need to add the `extension=phalcon.so` in your `php.ini` both for CLI and web server.

#### Tuning Build

By default we compile to be as compatible as possible with all processors (`gcc -mtune=native -O2 -fomit-frame-pointer`). If you would like instruct the compiler to generate optimized machine code that matches the processor where it is currently running on you can set your own compile flags by exporting CFLAGS before the build. For example

    export CFLAGS="-march=native -O2 -fomit-frame-pointer"
    zephir build
    

This will generate the best possible code for that chipset but will likely break the compiled object on older chipsets.

### 공유 호스팅

Running your application on shared hosting might restrict you in installing Phalcon, especially if you do not have root access. Some web hosting control panels luckly have Phalcon support.

#### cPanel & WHM

cPanel & WHM support Phalcon using Easy Apache 4 (EA4). You can install Phalcon by enabling the [module](https://github.com/CpanelInc/scl-phalcon) in Easy Apache 4 (EA4).

#### Plesk

The plesk control panel doesn't have Phalcon support but you can find installation instructions on the Plesk [website](https://support.plesk.com/hc/en-us/articles/115002186489-How-to-install-Phalcon-framework-for-a-PHP-supplied-by-Plesk-)