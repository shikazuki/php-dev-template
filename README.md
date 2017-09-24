# php-dev-template
Open source software development of php with docker, for example magento.
To work with docker toolbox, use ftp for file synchronize.

## Requirements
- docker toolbox
- docker for windows
- docker for mac

## Starting
```shell
$ docker-compose up -d --build
```

## Synchronize code
Synchronize files with your code using sftp.   
This repository uses docker image 'atmoz/sftp'. Use port `2222` to synchronize files.
