# Docker-PHP-Analysis, PHP Static Code Analysis

Docker-PHP-Analysis is a PHP Static Code Analysis Tool.

## Depends On

- [phan](https://github.com/etsy/phan)
- [PHPMD](https://github.com/phpmd/phpmd)
- [PhpMetrics](https://github.com/phpmetrics/PhpMetrics)

## Getting Started

```bash

$ git clone https://github.com/recruit-sumai/docker-php-analysis.git
$ cd docker-php-analysis
$ cp -r {your project} src/

```

## phan

```bash
$ docker build -t phantool ./phan
$ docker run --rm --volume `pwd`/src:/var/www/html phantool /bin/bash -c 'find ./{your project src} -name "*.php" -type f | xargs /tools/vendor/bin/phan > _report/phan.log'
```

Open Your Editor `src/_report/phan.log`

## PHPMD

```bash
$ docker build -t phpmdtool ./phpmd
$ docker run --rm --volume `pwd`/src:/var/www/html phpmdtool /bin/bash -c '/tools/vendor/bin/phpmd --strict ./{your project src} text cleancode,codesize,controversial,design,naming,unusedcode > _report/phpmd.log'
```

Open Your Editor `src/_report/phpmd.log`

## PhpMetrics

```bash
$ docker build -t phpmetricstool ./phpmetrics
$ docker run --rm --volume `pwd`/src:/var/www/html phpmetricstool /bin/bash -c '/tools/vendor/bin/phpmetrics  --report-html=./_report/phpmetrics ./{your project src}'
```

Open Your Browser `src/_report/phpmetrics/index.html`
