[![Version](http://img.shields.io/packagist/v/bit3/assetic-autoprefixer.svg?style=flat-square)](https://packagist.org/packages/bit3/assetic-autoprefixer)
[![Stable Build Status](http://img.shields.io/travis/bit3/assetic-autoprefixer/master.svg?style=flat-square)](https://travis-ci.org/bit3/assetic-autoprefixer)
[![Upstream Build Status](http://img.shields.io/travis/bit3/assetic-autoprefixer/develop.svg?style=flat-square)](https://travis-ci.org/bit3/assetic-autoprefixer)
[![License](http://img.shields.io/packagist/l/bit3/assetic-autoprefixer.svg?style=flat-square)](https://github.com/bit3/assetic-autoprefixer/blob/master/LICENSE)
[![Downloads](http://img.shields.io/packagist/dt/bit3/assetic-autoprefixer.svg?style=flat-square)](https://packagist.org/packages/bit3/assetic-autoprefixer)

Autoprefixer filter
===================

This is a filter implementation to use [Autoprefixer](https://github.com/postcss/autoprefixer)
within the [PHP assetic framework](https://github.com/kriswallsmith/assetic).

Requirements
------------

[`kriswallsmith/assetic`](https://github.com/kriswallsmith/assetic) is required to be installed in your php project.
[`postcss/autoprefixer`](https://github.com/postcss/autoprefixer) is required to be installed on your system.

### Install kriswallsmith/assetic with composer

```bash
php composer.phar require kriswallsmith/assetic ~1.0
```

### Install autoprefixer globally on your system

```bash
sudo npm install -g autoprefixer
```

### Install autoprefixer locally on your system

```bash
npm install autoprefixer
```

Usage in PHP
------------

```php
use Bit3\Assetic\Filter\Autoprefixer\AutoprefixerFilter;

// if you have installed autoprefixer globally
$autoprefixerBinary = '/usr/bin/autoprefixer';

// if you have installed autoprefixer locally
$autoprefixerBinary = '/../node_modules/.bin/autoprefixer';

$autoprefixerFilter = new AutoprefixerFilter($autoprefixerBinary);

// if node.js binary is not installed as /usr/bin/node
// (e.g. on debian/ubuntu the binary is named /usr/bin/nodejs)
$autoprefixerFilter->setNodeBin('/usr/bin/nodejs');
```

Usage in Symfony2
-----------------

This project comes with a assetic filter configuration file, located in the `config` directory.

Define the autoprefixer binary path in the `parameters.yml`:

```yaml
parameters:
  # if you have installed autoprefixer globally
  assetic.autoprefixer.bin: /usr/bin/autoprefixer

  # if you have installed autoprefixer locally
  assetic.autoprefixer.bin: %kernel.root_dir%/../node_modules/.bin/autoprefixer

  # if node.js binary is not installed as /usr/bin/node
  # (e.g. on debian/ubuntu the binary is named /usr/bin/nodejs)
  assetic.node.bin: /usr/bin/nodejs
```

Then enable the filter in the `assetic` configuration chapter:

```yaml
# Assetic Configuration
assetic:
    filters:
        autoprefixer:
          resource: "%kernel.root_dir%/../vendor/netzmacht/assetic-autoprefixer/config/autoprefixer.xml"
          # if you like, you can use apply_to here :-)
          # e.g, apply_to: "\.css"
          # otherwise you use the filter in your template with filter="autoprefixer"
```
