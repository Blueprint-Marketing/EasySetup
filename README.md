# OpenWP EasySetup for WordPress

__OpenWP EasySetup__ (es) is command-line setup tool with __Markdown config files__ using __[WP-CLI](http://wp-cli.org)__

For WordPress Installation use [EasyEngine](https://github.com/rtCamp/easyengine)

OpenWP EasySetup is tested on __Ubuntu__ and __Debian__.

## Installation

```sh
sudo apt-get install jq
git clone https://github.com/OpenWP/easysetup
cd easysetup
chmod +x es.sh
sudo cp es.sh /usr/local/bin/es
```

### Markdown Config Files

- [commands.md](https://github.com/OpenWP/easysetup/blob/master/commands.md)
- [constants.md](https://github.com/OpenWP/easysetup/blob/master/constants.md)
- [options.md](https://github.com/OpenWP/easysetup/blob/master/options.md)
- [getoptions.md](https://github.com/OpenWP/easysetup/blob/master/getoptions.md)
- [plugins.md](https://github.com/OpenWP/easysetup/blob/master/plugins.md)
- [themes.md](https://github.com/OpenWP/easysetup/blob/master/themes.md)
- [variables.md](https://github.com/OpenWP/easysetup/blob/master/variables.md)

Copy this config files to SITE_ROOT/setup (/var/www/example.com/setup)

```sh
mkdir /var/www/example.com/setup
sudo cp *.md /var/www/example.com/setup
```

__Customize Config Files before run OpenWP EasySetup!__

You can create whatever config files thanks to __wildcard__ (commands*.md).

### Changeable Variables

Variables are in file [es.sh](https://github.com/OpenWP/easysetup/blob/master/es.sh)

```sh
LOG_DIR=/var/log/easysetup
ES_LOG=$LOG_DIR/es.log

DOCUMENT_ROOT=/var/www
DOCUMENT_USER=www-data
# Regex for exclude markdown and blank lines from config files
REGEX_MARKDOWN="^#|^-|^\*|^\`|^$"
SSL_DAYS=3650

SITE_ROOT=$DOCUMENT_ROOT/$DOMAIN

WP_CERT=$SITE_ROOT/cert
WP_CONFIG=$SITE_ROOT/wp-config.php
WP_ROOT=$SITE_ROOT/htdocs

WP_COMMANDS=$SITE_ROOT/setup/commands*.md
WP_CONSTANTS=$SITE_ROOT/setup/constants*.md
WP_OPTIONS=$SITE_ROOT/setup/options*.md
WP_GETOPTIONS=$SITE_ROOT/setup/getoptions*.md
WP_PLUGINS=$SITE_ROOT/setup/plugins*.md
WP_THEMES=$SITE_ROOT/setup/themes*.md
WP_VARIABLES=$SITE_ROOT/setup/variables*.md

SSL_EMAIL=admin@$DOMAIN
SSL_COUNTRY=$(echo "$DOMAIN" | rev | cut -d'.' -f1 | rev)
```

## Usage

```sh
sudo es [Options] <domain>
  all <domain>: Run All Tasks
  commands <domain>: Run WP-CLI Commands
  constants <domain>: Set WP Constants
  cron <domain>: Set Crontab
  help: Show Help
  options <domain>: Set WP Options
  getoptions <domain>: Get WP Options in JSON Format
  plugins <domain>: Install WP Plugins
  ssl <domain>: Create Self-signed SSL Certificate
  themes <domain>: Install WP Themes
  update <domain>: Update WP Core, Plugins, Themes
  variables <domain>: Set Variables in WP Options
```

## MIT License

The MIT License (MIT) Copyright (c) 2014 OpenWP [openwp.github.io](http://openwp.github.io)

