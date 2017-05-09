# Docker-PHP-Analysis, PHP Static Code Analysis

Docker-PHP-Analysis is a PHP Static Code Analysis Tool.

## Depends On

- [phan](https://github.com/etsy/phan)
- [PHPMD](https://github.com/phpmd/phpmd)
- [PhpMetrics](https://github.com/phpmetrics/PhpMetrics)

## Install dependency tools
- [whalebrew](https://github.com/bfirsh/whalebrew)

## Getting Started

```bash

$ git clone https://github.com/recruit-sumai/docker-php-analysis.git
$ cd docker-php-analysis
$ cp -r {your project} src/

```

## phan

```bash
For dokcer

# Building
$ docker build -t phantool ./phan

# Analyzing
$ docker run -it -v "$(pwd)":/workdir phantool -l ./src/{your project src} > ./src/_report/phan.log


# Debugging
$ docker run --rm -v "$(pwd)":/workdir -it --entrypoint=bash phantool
```

```bash
For whalebrew

# install(local docker image)
$ docker build -t phantool ./phan
$ whalebrew install phantool

# Analyzing
$ phan -l ./src/{your project src} > ./src/_report/phan.log
```

Open Your Editor `src/_report/phan.log`

## PHPMD

```bash
For dokcer

# Building
$ docker build -t phpmdtool ./phpmd

# Analyzing
$ docker run -it -v "$(pwd)":/workdir phpmdtool --strict ./src/{your project src} text cleancode,codesize,controversial,design,naming,unusedcode > ./src/_report/phpmd.log


# Debugging
$ docker run --rm -v "$(pwd)":/workdir -it --entrypoint=bash phpmdtool
```

```bash
For whalebrew

# install(local docker image)
$ docker build -t phpmdtool ./phpmd
$ whalebrew install phpmdtool

# Analyzing
$ phpmd  --strict ./src/{your project src} text cleancode,codesize,controversial,design,naming,unusedcode > ./src/_report/phpmd.log
```

Open Your Editor `src/_report/phpmd.log`

## PhpMetrics

```bash
For dokcer

# Building
$ docker build -t phpmetricstool ./phpmetrics

# Analyzing
$ docker run -it -v "$(pwd)":/workdir phpmetricstool --report-html=./src/_report/phpmetrics ./src/{your project src}


# Debugging
$ docker run --rm -v "$(pwd)":/workdir -it --entrypoint=bash phpmetricstool
```

```bash
For whalebrew

# install(local docker image)
$ docker build -t phpmetricstool ./phpmetrics
$ whalebrew install phpmetricstool

# Analyzing
$ phpmetrics --report-html=./src/_report/phpmetrics ./src/{your project src}
```

Open Your Browser `src/_report/phpmetrics/index.html`
