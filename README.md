### Установка Яндекс Браузера в VoidLinux
### Install yandex-browser in VoidLinux

Склонировать `void-packages` в любую домашнюю директорию и установить окружение для сборки пакетов:
```
git clone https://github.com/void-linux/void-packages.git
cd void-packages
./xbps-src binary-bootstrap
```

Чтобы собрать пакет с пометкой "restricted":
```
echo XBPS_ALLOW_RESTRICTED=yes >> etc/conf
```

Клонируем репозиторий:
```
cd srcpkgs
git clone https://github.com/MrAiupov/yandex-browser/
cd ../
```

Собираем Яндекс Браузер:
```
./xbps-src pkg yandex-browser
```

Устанавливаем Яндекс Браузер:
```
xbps-install -v --repository hostdir/binpkgs/nonfree yandex-browser
```

Как обновить пакет (при условии что обновлён template в данном репозитории)
```
cd void-packages
cd srcpkgs
git clone https://github.com/MrAiupov/yandex-browser/
./xbps-src pkg yandex-browser
xbps-install -v --repository hostdir/binpkgs/nonfree yandex-browser
```

Либо вы можете сами обновите шаблон template.
Нужно перейти по адресу https://repo.yandex.ru/yandex-browser/deb/pool/main/y/yandex-browser-stable/
И также перейти по адресу в вашей домашней директории, в которую клонировали void-packages/srcpkgs/yandex-browser, и открыть наш файл `template`
Сверить версию установочного deb файла с сайта, с указанной версией в строке `version` в файле `template`.
И если вышло обновление, скачать данный deb файл с сайта и вычислить хешсумму SHA1 установочного deb файла.
И изменить две строки в файле `template`, это строку version указав новую версию (до первого тире) и обновить строку `checksum` указав новую хэшсумму файла, сохранить.
После этого открыть консоль и ввести, и браузер обновиться до новой версии.
```
cd void-packages
cd srcpkgs
./xbps-src pkg yandex-browser
xbps-install -v --repository hostdir/binpkgs/nonfree yandex-browser
```
