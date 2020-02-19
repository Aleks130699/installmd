# installmd

Скрипт установки MajorDoMo на OrangePi, Asus Tinker Board, RaspberryPi, Cubieboard, NanoPi, BananaPi и т.п.

Установка.

sudo su

apt-get update

apt-get upgrade 

wget https://raw.githubusercontent.com/immortalserg/installmd/master/installmd 

chmod +x ./installmd

./installmd параметры

### Параметры:

нет параметров - справка.

-h - справка

-t - установка базовой системы MAjorDoMo c вэб сервером apache

-x - установка базовой системы MAjorDoMo c вэб сервером nginx + php-fpm (вместо флага -t)

-c [path] - альтернативная конфигурация, параметр не обязательный, если не указан, то конфигурация базовая, path - путь к своей конфигурации (если путь не задан то устанавливается расширенная конфигурация)

-b - установка/обновление Blynk сервера, устанавливает или обновляет автоматически последнюю версию Blynk server

-j - установка Java

-a - установить webmin

-n - установить node.js из исходников (установка долгая 2-3 часа)

-o [type [port]]  - установить owfs. type - тип 1-wire адаптера (usb, uart, i2c), port - порт uart 1-wire адаптера без /dev/ (ttyS2*, ttyUSB...)

-r - установить RHVoice

-w [type] - установить WiringPi. [type] - тип платы: 1 - OrangePi, 2 - Asus tinker board, 3 - RaspberryPi, 4 - BananaPi, 5 - NanoPi, 6 - Cubieboard2, 7 - BananaPro

-e - установить MySensors

-v - VPN клиент OpenVPN

-m - MQTT сервер и клиент Mosquitto

-u - 433Utils

-p - phpMyAdmin (установка или обновление)

-s - оптимизация работы с SD картой (база в tmpfs)

-d - часы реального времени DS3132 на i2c

-l - отключение логов

Возможна установка компонентов по отдельности.

Для работы системы Majordomo достаточно установить только с флагом -t.

ВНИМАНИЕ!!! при установке системы с флагом -t пароли вводятся либо в коммандной строке, либо в самом начале на запрос ввести пароль желтыми буквами

Введите пароль root для MariaDB (MySQL) > 

Введите пароль пользователя pi (для пользователя системы и пользователя базы данных MajorDoMo) > 

и больше нигде не вводить пароль, во время установки базы данных выйдет окно пароля, не вводить пароль просто нажать дальше (enter)
 
### Примеры использования

./installmd -t  - установка базовой системы с стандартной конфигурацией

./installmd -t -с  - установка базовой системы с расширенной конфигурацией

./installmd -t -с /home/user/backup.tgz  - установка базовой системы с своей конфигурацией архив которой находиться по пути /home/user/backup.tgz 

./installmd -t -с ./backup.tgz -  установка базовой системы с своей конфигурацией архив которой находиться в папке с скриптом установки

./installmd -t -p - установка базовой системы и phpMyAdmin

./installmd -t -p -j - установка базовой системы, phpMyAdmin, Java

./installmd -j - установка Java

./installmd -n - установка node.js

### Исправления.

v.0.5.4 от 02.10.2019
- исправлен конфиг nginx (не работала функция API) 
- добавлено в конец установки apache включение a2enmod php7.x

v.0.5.3 от 28.02.2019
- исправлено добавление репозитариев mariadb-server

v.0.5.2 от 13.02.2019
- исправлена ошибка загрузки больших файлов при установке nginx

v.0.5.1 от 01.02.2019
- определение пути к php-fpm при установке nginx
- включение портов i2c, uart, spi и аудио выхода
- исправлена ошибка при старте php модуля в apache

v.0.5.0 от 18.01.2019
- установка nginx с флагом -x (вместо -t)

v.0.4.12 от 14.01.2019
- исправлено отсутствуие звуковой карты
- задается DNS имя md.lan

v0.4.11 от 10.01.2019
- добавлено в функцию отключение логов отключение journald

v0.4.10 от 05.01.2019
- добавлен запуск Blynk сервер
- убран ввод пароля из коммандной строки

v0.4.9 от 25.11.2018
- обновление phpmyadmin
- исправлено удаление каталогов после установки

v0.4.8 от 15.11.2018
- добавлено определение системы и добавление соответствующих репозитариев mariadb
- исправлены ошибки установки в Debian и Ubuntu 18.10

v0.4.7 от 11.11.2018
- установка/обновление Blynk server
- исправления
- добавлено отключение логов, запуск с ключем -l

v0.4.6 от 24.10.2018
- настройка параметров в php7.2

v.0.4.5 от 19.10.2018
- исправлена ошибка с правами на файлы и папки при расширенной конфигурации (https://github.com/immortalserg/installmd/issues/2)
- убраны лишние пакеты php (https://github.com/immortalserg/installmd/pull/3)
- добавлена установка snmp-mibs-downloader

v.0.4.4 от 10.10.2018
- исправлена ошибка при установке базы данных
- добавлено сообщение о паролях

v.0.4.3 от 04.10.2018
- исправлена ошибка при выборе нескольких флагов с параметрами

v.0.4.2 от 01.10.2018
- убраны одинаковые флаги
- исправлена ошибка в скрипте при установке WiringPi

v.0.4.1 от 29.09.2018
- скрипт работает с параметрами коммандной строки
- исправлена ошибка неудовлетворенных зависимостей при установке mariadb-server

v.0.3.13 от 18.09.2018
- запуск vlc сервисом
- установка RHVoice

v.0.3.12 от 16.09.2018
- добавление репозитария Universe в Ubuntu Server
- добавление репозитария MariaDB
- проверка и установка php7.2
- проверка наличия /etc/rc.local и при отсутствии добавление и включение его в автозагрузку

v.0.3.11
- исправлен запуск MajorDoMo не от root, а от www-data
- исправлена расширенная конфигурация

v.0.3.10
- увеличен размер раздела /run до 4M
- добавлен пункт выбора x86 AMD64 с запретом оптимизации работы с картой памяти
- добавлен в /etc/rc.local старт mysql с паузой (закомментирован)


v.0.3.9
- исправлена "проглатывание" начала фраз, в pulse включает выход когда появляется звук, исправление комментированием в /etc/pulse/default.pa параметра load-module module-suspend-on-idle


v.0.3.8
- исправлена расширенная конфигурация, база расширенной конфигурации в MyISAM, InnoDB запрещена
- не создается файл asound.conf для RaspberryPi3 (были из-за него проблемы со звуком на RaspberryPi3)

v.0.3.7
- конвертация таблиц только при расширенной конфигурации
- некоторые исправления в скриптах запуска
- исправлено внесение изменений в php.ini

v.0.3.6
- исправлен asound.conf, было невозможно использовать одновременно онлайн радио и проговаривание Алисы

v.0.3.5
- добавлена проверка версии php для возможности установки
- проверка возможности установки mariadb
- диалог выбора оптимизации базы данных

v.0.3.4
- добавлена проверка установки на DietPi, в DietPi php версии 5 и установка возможна только указывая версию, репозитарии 7-й версии не добавляются, в скрипт добавлена проверка установки на DietPi и установку php5

v.0.3.3
- добавлено предупрежджение о запрете ввода паролей для базы данных после всех ответов в начале скрипта и ввода паролей базы в скрипте.
- добавлен поиск конфигурационного файла в /etc/mysql (до исправления конфиг был прописан в одном месте что вызывало проблемы когда в системе конфигурационный файл лежит в другом)

v.0.3.2
- запрос на выбор конвертировать таблицы из InnoDB в MyISAM

v.0.3.1
- исправлено зависание в Debian не отрабатывала команда apt-key add с ключем-qq
- в Debian отсутствует пакет apt-add-repository, добавлена установка.

v.0.3
- возможность установки своего бэкапа
- база данных в MyISAM, конвертация всех таблиц из InnoDB в MyISAM, InnoDB отключена

v.0.2.2
- часы реального времени DS3231

v.0.2.1
- добавлено комментирование /tmp в /etc/fstab до вставки 
- добавлено в fstab монтирование /run в tmpfs
- добавлена проверка блокировки /var/lib/dpkg/lock и занятости другим процессом apt
- добавлено проверка повторного добавления репов в sources.list при повторном запуске скрипта 
