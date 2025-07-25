## Установка Яндекс Браузера в VoidLinux

### 1. Клонирование void-packages и настройка xbps-src

Клонировать `void-packages` в любую домашнюю директорию и установить окружение для сборки пакетов:
```
$ git clone https://github.com/void-linux/void-packages.git
$ cd void-packages
$ ./xbps-src binary-bootstrap
```

Чтобы собрать пакет с пометкой "restricted":
```
$ echo XBPS_ALLOW_RESTRICTED=yes >> etc/conf
```

### 2. Клонируем наш репозиторий, собираем и устанавливаем пакет yandex-browser

Клонирование репозитория с шаблоном установки `yandex-browser` для xpbs-src

```
$ cd srcpkgs
$ git clone https://github.com/MrAiupov/yandex-browser/
$ cd ../
```

Сборка `yandex-browser`
```
$ ./xbps-src pkg yandex-browser
```

Установка `yandex-browser`

```
$ sudo xbps-install -v --repository hostdir/binpkgs/nonfree yandex-browser
```

### 3. Обновление пакета yandex-browser (при условии что обновлён template в данном репозитории)

Вводим в консоли данные команды, где ранее был клонирован `void-packages`

```
$ cd void-packages
$ cd srcpkgs
$ git clone https://github.com/MrAiupov/yandex-browser/
$ ./xbps-src pkg yandex-browser
$ sudo xbps-install -v --repository hostdir/binpkgs/nonfree yandex-browser
```
### 4. Ручное обновление пакета yandex-browser

Вы можете сами обновить файл `template`, по которому вы ранее собирали пакет `yandex-browser`.

Для начала нужно удостовериться о наличии обновления пакета `yandex-browser`.

Нужно перейти по адресу https://repo.yandex.ru/yandex-browser/deb/pool/main/y/yandex-browser-stable/

И также открыть нашу старую директорию `./void-packages/srcpkgs/yandex-browser`, и открыть наш файл `template`

Сверить версию установочного deb файла с сайта, с указанной версией в строке `version` в файле `template`.

И если вышло обновление, скачать данный deb файл с сайта и вычислить хешсумму SHA1 установочного deb файла.

И изменить две строки в файле `template`, это строку `version` указав новую версию (до первого тире) и обновить строку `checksum` указав новую хэшсумму файла, и сохранить файл.

После этого открыть консоль и ввести данные команды, и `yandex-browser` обновится до новой версии.

```
$ cd void-packages
$ cd srcpkgs
$ ./xbps-src pkg yandex-browser
$ sudo xbps-install -v --repository hostdir/binpkgs/nonfree yandex-browser
```

При возникновении вопросов, вы можете их задать в нашем уютном чате по VoidLinux.
https://t.me/voidlinux_ru

Хорошего сёрфинга!
