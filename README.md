### Установка Яндекс Браузера в VoidLinux
### Install yandex-browser in VoidLinux

Склонировать `void-packages` и установить окружение для сборки пакетов:
```
$ git clone https://github.com/void-linux/void-packages.git
$ cd void-packages
$ ./xbps-src binary-bootstrap
```

Чтобы собрать пакет с пометкой "restricted":
```
$ echo XBPS_ALLOW_RESTRICTED=yes >> etc/conf
```

Клонируем репозиторий:
```
$ cd srcpkgs
$ git clone https://github.com/MrAiupov/yandex-browser/
$ cd ../
```

Собираем Яндекс Браузер:
```
$ ./xbps-src pkg yandex-browser
```

Устанавливаем Яндекс Браузер:
```
# xbps-install -v --repository hostdir/binpkgs/nonfree yandex-browser
