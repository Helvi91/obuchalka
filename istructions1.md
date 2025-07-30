# Основные команды Linux
## Оглавление:
[1.Команды для получения справки](#1-команды-для-получения-справки)

[2.Команды управления сетью](#2-команды-управления-сетью)

[3.Команды для управления файлами и директориями](#3-команды-для-управления-файлами-и-директориями)

[4.Команды для архивирования](#4-команды-для-архивирования)

[5.Команды для работы с текстом](#5-команды-для-работы-с-текстом)

[6.Команды для управления процессами](#6-команды-для-управления-процессами)

[7.Работа с пакетными менеджерами](#7-работа-с-пакетными-менеджерами)

[8.Команды управления пользователями](#8-команды-управления-пользователями)

[9.Команды выключения и перезагрузки](#9-команды-выключения-и-перезагрузки)

[10.Бонусные команды](#10-бонусные-команды)
## 1. Команды для получения справки:
### 1.1. man — manual, получение справки
Чтобы получить справку по команде, введите перед ней man. Например, man man выдаст руководство по команде man. Также можно вывести мануал терминала Linux (man bash):
 
 ```
 BASH(1)                                General Commands Manual                                BASH(1)

NAME

      bash - GNU Bourne-Again SHell

SYNOPSIS

      bash [options] [command_string | file]

COPYRIGHT

      Bash is Copyright (C) 1989-2018 by the Free Software Foundation, Inc.

DESCRIPTION

      Bash is  an  sh-compatible  command language interpreter that executes commands read from the
      standard input or from a file. Bash also incorporates useful features from  the  Korn  and  C
      shells (ksh and csh).

      Bash  is  intended to be a conformant implementation of the Shell and Utilities portion of the
      IEEE POSIX specification (IEEE Standard 1003.1).  Bash can be configured to  be  POSIX-confor‐
      mant by default.

OPTIONS

      All  of  the  single-character  shell options documented in the description of the set builtin
      command, including -o, can be used as options when the shell is invoked.   In  addition,  bash
      interprets the following options when it is invoked:
      -c        If  the -c option is present, then commands are read from the first non-option argu‐
                ment command_string.  If there are arguments after the command_string, the first ar‐
                gument  is assigned to $0 and any remaining arguments are assigned to the positional;
```

### 1.2. help - вызов краткой справки
Данная команда используется для вызова краткой справки:
```
history: history [-c] [-d смещение] [n] или history -anrw [**файл**] или history -ps аргумент [аргумент...]

   Display or manipulate the history list.
    
   Display the history list with line numbers, prefixing each modified
   entry with a `*'.  An argument of N lists only the last N entries.
    
   Options:

     -c        clear the history list by deleting all of the entries
     -d offset delete the history entry at position OFFSET. Negative
               offsets count back from the end of the history list
    
     -a        append history lines from this session to the history file
     -n        read all history lines not already read from the history file
               and append them to the history list
     -r        read the history file and append the contents to the history
               list
     -w        write the current history to the history file
    
     -p        perform history expansion on each ARG and display the result
               without storing it in the history list
     -s        append the ARGs to the history list as a single entry
    
   If FILENAME is given, it is used as the history file.  Otherwise,
   if HISTFILE has a value, that is used, else ~/.bash_history.
    
   If the HISTTIMEFORMAT variable is set and not null, its value is used
   as a format string for strftime(3) to print the time stamp associated;
```
   _Другой вариант — вывод справки через специальные ключи — **команда -h** или **команда —help**_
### 1.3. Tab — автозавершение команды
Отображает доступные варианты завершения команды:
```
debtop@DebTop:~$ cd                  

.aptitude/     .gnupg/        .mozilla/      Видео/         Изображения/   Рабочий стол/

.cache/        .kde/          .pki/          Документы/     Музыка/        Шаблоны/

.config/       .local/        snap/          Загрузки/      Общедоступные/  

debtop@DebTop:~$ cd .

./         .aptitude/ .config/   .kde/      .mozilla/   
../        .cache/    .gnupg/    .local/    .pki/ ;
```
### 1.4.cat /etc/*-release — отображение дистрибутива. 
Команда показывает, какой дистрибутив установлен на данном устройстве.При запросе выдается основная информация - имя, версия и др.:
```
debtop@DebTop:~$ cat /etc/*-release

PRETTY_NAME="Debian GNU/Linux 10 (buster)"

NAME="Debian GNU/Linux"

VERSION_ID="10"

VERSION="10 (buster)"

VERSION_CODENAME=buster

ID=debian

HOME_URL="https://www.debian.org/"

SUPPORT_URL="https://www.debian.org/support"

BUG_REPORT_URL="https://bugs.debian.org/"

debtop@DebTop:~$ lsb_release -a

No LSB modules are available.

Distributor ID: Debian

Description:    Debian GNU/Linux 10 (buster)

Release:        10

Codename:       buster

debtop@DebTop:~$ lsb_release -i

Distributor ID: Debian 
```
_Аналогами в данном случае будут являться **lsb_release -a**, которая выведет почти ту же информацию, а **lsb_release -i** напишет ID дистрибутива._
### 1.5. whoami - отображение  текущего пользователя
Команда отображает имя текущего пользователя:
```
debtop@DebTop:~$ whoami

desktop
```
### 1.6. whatis - отображение информации программе
Выводит краткую информацию о любой установленной программе:
```
debtop@DebTop:~$ whatis nano
nano (1)             
- Nano's ANOther editor, an enhanced free Pico clone

debtop@DebTop:~$ whatis apt
apt (8)           
- command-line interface
```
При этом следует учесть, что при введении наименования неустановленной программы, то описание не будет выведено:

``` 
debtop@DebTop:~$ whatis krita

krita: ничего подходящего не найдено. 
```
### 1.7. whereis — полный путь к программе
Команда для просмотра полного пути к исполняемому файлу программы:
```  
debtop@DebTop:~$ whereis bash

bash: /usr/bin/bash /etc/bash.bashrc /usr/share/man/man1/bash.1.gz
```
## 2. Команды управления сетью:
### 2.1. hostname, ifconfig — управление сетью
Предназначены для просмотра DNS-домена и IP-адреса компьютера.
```  
debtop@DebTop:~$ hostname
DebTop 
debtop@DebTop:~$ hostname -i
127.0.1.1
debtop@DebTop:~$ ifconfig
bash: ifconfig: команда не найдена
```
_Некоторые версии дистрибутивов Linux поддерживают команду **ifconfig**, которая также выводит текущий IP, но она работает не всегда. Вместо ifconfig современные дистрибутивы отзываются на **ip a[ddress]**, которая выведет на экран настройки сети и позволяет их редактировать. Команда является частью пакета утилит для настройки параметров сетевых устройств — **iproute2**. Команды из набора iproute2 используются для создания доменной сети._
```  
debtop@DebTop:~$ ip a

1: lo:  mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
   link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
   inet 127.0.0.1/8 scope host lo
      valid_lft forever preferred_lft forever
   inet6 ::1/128 scope host  
      valid_lft forever preferred_lft forever

2: enp4s0:  mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1
000
   link/ether b4:b5:2f:7f:fe:eb brd ff:ff:ff:ff:ff:ff

3: wlo1:  mtu 1500 qdisc mq state UP group default qlen 1000
   link/ether a4:17:31:2a:bc:59 brd ff:ff:ff:ff:ff:ff
   inet 192.168.1.195/24 brd 192.168.1.255 scope global dynamic noprefixroute wlo1
      valid_lft 85273sec preferred_lft 85273sec
   inet6 fe80::3f0f:a837:e4c0:e52d/64 scope link noprefixroute  
      valid_lft forever preferred_lft forever

debtop@DebTop:~$ ip

Usage: ip [ OPTIONS ] OBJECT { COMMAND | help }
      ip [ -force ] -batch filename

where  OBJECT := { link | address | addrlabel | route | rule | neigh | ntable |
                  tunnel | tuntap | maddress | mroute | mrule | monitor | xfrm |
                  netns | l2tp | fou | macsec | tcp_metrics | token | netconf | ila |
                  vrf | sr }

      OPTIONS := { -V[ersion] | -s[tatistics] | -d[etails] | -r[esolve] |
                   -h[uman-readable] | -iec | -j[son] | -p[retty] |
                   -f[amily] { inet | inet6 | ipx | dnet | mpls | bridge | link } |
                   -4 | -6 | -I | -D | -M | -B | -0 |
                   -l[oops] { maximum-addr-flush-attempts } | -br[ief] |
                   -o[neline] | -t[imestamp] | -ts[hort] | -b[atch] [filename] |
                   -rc[vbuf] [size] | -n[etns] name | -a[ll] | -c[olor]}
```
### 2.2. ping — диагностика неисправностей сети
Ping используется для поиска неисправностей, тестирования и диагностики сетевых соединений,позволяет определить задержку сообщений или потерю пакетов.

_Достаточно ввести, например, **ping google.com**, компьютер сам определит IP адрес домена и продолжит выполняться, пока ее не отменить сочетанием Ctrl+C._
## 3. Команды для управления файлами и директориями:
### 3.1. mkdir — создание директории
Из домашней директории пользователя вводится в bash:
**mkdir playpen**

Далее проверка наличия директории:

**ls — list** - отображение директории и файлов
_Чтобы убедиться в наличии директории нужно набрать **ls**, после выполнения команда покажет все каталоги и файлы._
```    
debtop@DebTop:~$ mkdir playpen

debtop@DebTop:~$ ls

playpen   Видео       Загрузки      Музыка         'Рабочий стол'

snap      Документы   Изображения   Общедоступные   Шаблоны
```
### 3.2. cd — change directory, смена директории
Для навигации в терминале Linux нужно ввести cd имя_директории. 
```
debtop@DebTop:~$ cd playpen

debtop@DebTop:~/playpen$
```
_Если работа в данной директории закончена и необходимо подняться на уровень вверх из текущей директории, используйте «cd пробел .. (две точки)»:_
**cd ..**
_Для перемещения между двумя директориями  используется быстрый переход к предыдущей директории «cd пробел — (дефис)»:_
**cd —**
```
debtop@DebTop:~/playpen/dir00$ cd /usr/lib/x86_64-linux-gnu/audacious
 
debtop@DebTop:/usr/lib/x86_64-linux-gnu/audacious$ cd - 

/home/debtop/playpen/dir00
 
debtop@DebTop:~/playpen/dir00$ cd -

/usr/lib/x86_64-linux-gnu/audacious
 
debtop@DebTop:/usr/lib/x86_64-linux-gnu/audacious$ cd -

/home/debtop/playpen/dir00
 
debtop@DebTop:~/playpen/dir00$ cd ..
```
### 3.3. pwd — Быстрый просмотр текущей директории
Быстрый просмотр текущей директории. 
### 3.4. mkdir dir{00..42} -быстрое одновременное создание нескольких директорий
**mkdir** создает директорию, **dir** задает начальное имя для каждой новой директории, числа в фигурных скобках **{00..42}** указывают переменную часть имени создаваемых папок.
Проверка наличия созданных папок производится через команду **ls**.
```   
debtop@DebTop:~/playpen$ ls

dir00  dir03  dir06  dir09  dir12  dir15  dir18  dir21  dir24  dir27  dir30  dir33  dir36  dir39  dir42

dir01  dir04  dir07  dir10  dir13  dir16  dir19  dir22  dir25  dir28  dir31  dir34  dir37  dir40

dir02  dir05  dir08  dir11  dir14  dir17  dir20  dir23  dir26  dir29  dir32  dir35  dir38  dir41
```
### 3.5. touch - создание файлов и задать время последнего изменения
Для создания файлов и размещения их в конкретных директориях используется команда:

**touch dir{00..42}/text{00..42}.txt**
```
debtop@DebTop:~/playpen$ touch dir{00..43}/text{00..43}.txt

debtop@DebTop:~/playpen$ ls dir00

text00.txt  text06.txt  text12.txt  text18.txt  text24.txt  text30.txt  text36.txt  text42.txt

text01.txt  text07.txt  text13.txt  text19.txt  text25.txt  text31.txt  text37.txt  text43.txt

text02.txt  text08.txt  text14.txt  text20.txt  text26.txt  text32.txt  text38.txt

text03.txt  text09.txt  text15.txt  text21.txt  text27.txt  text33.txt  text39.txt

text04.txt  text10.txt  text16.txt  text22.txt  text28.txt  text34.txt  text40.txt

text05.txt  text11.txt  text17.txt  text23.txt  text29.txt  text35.txt  text41.txt
```
Также для создания файлов может быть использована команда **&gt; имя_файла** 

_**<>** это символы перенаправления или связи. Если перед именем несуществующего файла поставить знак > вместе с указанием расширения файла, в текущей директории появится пустой файл._
### 3.6. rm — remove, удаление
Чтобы удалить какой-либо файл, достаточно ввести команду **rm** с именем файла:
```
rm text00.txt
```
Можно удалить несколько:
```
rm text{01..12}.txt
```
### 3.7. rmdir - команда используется для удаления каталогов
Позволяет удалить каталог без содержимого.
```
rmdir delete_me
```
_Команда не позволит удалить каталог, в котором есть что-то еще — файл или другой каталог (даже пустой)_
### 3.8. rm с опцией рекурсивного удаления -r
Используется для удаления каталогов с содержимым.
```
rm -r ../dir03
```
_Все описанные переходы по директориям, упомянутые в описании команды **cd** действуют и для **rm**. Поэтому, при нахождении в подкаталоге **dir01**, команда будет выглядеть вот так:_
```    
debtop@DebTop:~/playpen/dir01$ rm text00.txt

debtop@DebTop:~/playpen/dir01$ rm text{01..12}.txt

debtop@DebTop:~/playpen/dir01$ mkdir delete_me

debtop@DebTop:~/playpen/dir01$ ls

delete_me   text16.txt  text20.txt  text24.txt  text28.txt  text32.txt  text36.txt  text40.txt

text13.txt  text17.txt  text21.txt  text25.txt  text29.txt  text33.txt  text37.txt  text41.txt

text14.txt  text18.txt  text22.txt  text26.txt  text30.txt  text34.txt  text38.txt  text42.txt

text15.txt  text19.txt  text23.txt  text27.txt  text31.txt  text35.txt  text39.txt

debtop@DebTop:~/playpen/dir01$ rm delete_me

rm: невозможно удалить 'delete_me': Это каталог

debtop@DebTop:~/playpen/dir01$ rmdir delete_me

debtop@DebTop:~/playpen/dir01$ ls

text13.txt  text17.txt  text21.txt  text25.txt  text29.txt  text33.txt  text37.txt  text41.txt

text14.txt  text18.txt  text22.txt  text26.txt  text30.txt  text34.txt  text38.txt  text42.txt

text15.txt  text19.txt  text23.txt  text27.txt  text31.txt  text35.txt  text39.txt

text16.txt  text20.txt  text24.txt  text28.txt  text32.txt  text36.txt  text40.txt

debtop@DebTop:~/playpen/dir01$ rmdir ../dir03

rmdir: не удалось удалить '../dir03': Каталог не пуст

debtop@DebTop:~/playpen/dir01$ rm -r ../dir03

debtop@DebTop:~/playpen/dir01$ ls ..

dir00  dir04  dir07  dir10  dir13  dir16  dir19  dir22  dir25  dir28  dir31  dir34  dir37  dir40

dir01  dir05  dir08  dir11  dir14  dir17  dir20  dir23  dir26  dir29  dir32  dir35  dir38  dir41

dir02  dir06  dir09  dir12  dir15  dir18  dir21  dir24  dir27  dir30  dir33  dir36  dir39  dir42
```
### 3.9. cp — copy, копирование
Кроме создания и удаления файлов и директорий терминал позволяет их копирование.

_Например из директории dir02 и скопировать файл text00.txt в директорию dir01:_
```
cp text00.txt /home/debtop/playpen/dir01
```
_Поскольку **text00.txt** находится в текущей директории, полный путь до него можно не указывать.Такое указание пути называется относительным. Путь до **dir01** в примере указан полностью, такой путь называется абсолютный. Можно указать просто **../dir01**, тогда это был бы снова относительный путь._
```
debtop@DebTop:~/playpen/dir01$ cd ../dir02

debtop@DebTop:~/playpen/dir02$ cp text00.txt home/debtop/playpen/dir01

cp: невозможно создать обычный файл 'home/debtop/playpen/dir01': Нет такого файла или каталога

debtop@DebTop:~/playpen/dir02$ cp text00.txt /home/debtop/playpen/dir01

debtop@DebTop:~/playpen/dir02$ ls ../dir01

text00.txt  text16.txt  text20.txt  text24.txt  text28.txt  text32.txt  text36.txt  text40.txt

text13.txt  text17.txt  text21.txt  text25.txt  text29.txt  text33.txt  text37.txt  text41.txt

text14.txt  text18.txt  text22.txt  text26.txt  text30.txt  text34.txt  text38.txt  text42.txt

text15.txt  text19.txt  text23.txt  text27.txt  text31.txt  text35.txt  text39.txt
```
_Каталоги копируются по тому же принципу, но необходимо добавление опции рекурсивного копирования_:
**cp -r dir00 dir03**
```
debtop@DebTop:~/playpen$ ls

dir00  dir04  dir07  dir10  dir13  dir16  dir19  dir22  dir25  dir28  dir31  dir34  dir37  dir40

dir01  dir05  dir08  dir11  dir14  dir17  dir20  dir23  dir26  dir29  dir32  dir35  dir38  dir41

dir02  dir06  dir09  dir12  dir15  dir18  dir21  dir24  dir27  dir30  dir33  dir36  dir39  dir42

debtop@DebTop:~/playpen$ cp dir00 dir03

cp: не указан -r; пропускается каталог 'dir00'

debtop@DebTop:~/playpen$ cp -r dir00 dir03

debtop@DebTop:~/playpen$ cp -r dir00 dir03/

debtop@DebTop:~/playpen$ cd dir03

debtop@DebTop:~/playpen/dir03$ ls

dir00       text05.txt  text11.txt  text17.txt  text23.txt  text29.txt  text35.txt  text41.txt

text00.txt  text06.txt  text12.txt  text18.txt  text24.txt  text30.txt  text36.txt  text42.txt

text01.txt  text07.txt  text13.txt  text19.txt  text25.txt  text31.txt  text37.txt

text02.txt  text08.txt  text14.txt  text20.txt  text26.txt  text32.txt  text38.txt

text03.txt  text09.txt  text15.txt  text21.txt  text27.txt  text33.txt  text39.txt

text04.txt  text10.txt  text16.txt  text22.txt  text28.txt  text34.txt  text40.txt
```
_Если при копировании каталога или файла в качестве адреса копирования указано имя несуществующей директории (или файла), то система автоматически создаст файл или каталог с таким именем._

_Для копирования только содержимого директории, указывается слэш после места назначения, а после него поставьте звездочку (*):_

***cp -r dir00/* dir03/dir**
### 3.10. mv, move — перемещение
Команда перемещает файлы и директории.

**mv что_перемещаем куда_перемещаем**
```
debtop@DebTop:~/playpen$ mv dir16 dir19/dir

debtop@DebTop:~/playpen$ ls dir19

dir         text05.txt  text11.txt  text17.txt  text23.txt  text29.txt  text35.txt  text41.txt

text00.txt  text06.txt  text12.txt  text18.txt  text24.txt  text30.txt  text36.txt  text42.txt

text01.txt  text07.txt  text13.txt  text19.txt  text25.txt  text31.txt  text37.txt

text02.txt  text08.txt  text14.txt  text20.txt  text26.txt  text32.txt  text38.txt

text03.txt  text09.txt  text15.txt  text21.txt  text27.txt  text33.txt  text39.txt

text04.txt  text10.txt  text16.txt  text22.txt  text28.txt  text34.txt  text40.txt
```
_Каталоги перемещаются их целиком так, при этом они перестают существовать в исходном местоположении._ 
Для перемещения содержимого каталогов  
### 3.11. —v[erbose] - для перемещения содержимого каталогов.
Перемещает всё содержимое папки (файлы, каталоги и файлы, вложенные в них), при этом папка остается пустой:

***mv -v dir19/* dir17/**
```
debtop@DebTop:~/playpen$ ls

dir00  dir04  dir08  dir12  dir17  dir21  dir25  dir29  dir33  dir37  dir41

dir01  dir05  dir09  dir13  dir18  dir22  dir26  dir30  dir34  dir38  dir42

dir02  dir06  dir10  dir14  dir19  dir23  dir27  dir31  dir35  dir39

dir03  dir07  dir11  dir15  dir20  dir24  dir28  dir32  dir36  dir40

debtop@DebTop:~/playpen$ man mv

debtop@DebTop:~/playpen$ ls dir19

dir         text05.txt  text11.txt  text17.txt  text23.txt  text29.txt  text35.txt  text41.txt

text00.txt  text06.txt  text12.txt  text18.txt  text24.txt  text30.txt  text36.txt  text42.txt

text01.txt  text07.txt  text13.txt  text19.txt  text25.txt  text31.txt  text37.txt

text02.txt  text08.txt  text14.txt  text20.txt  text26.txt  text32.txt  text38.txt

text03.txt  text09.txt  text15.txt  text21.txt  text27.txt  text33.txt  text39.txt

text04.txt  text10.txt  text16.txt  text22.txt  text28.txt  text34.txt  text40.txt

debtop@DebTop:~/playpen$ mv -v dir19/* dir17/

переименован 'dir19/dir' -&gt; 'dir17/dir'

переименован 'dir19/text00.txt' -&gt; 'dir17/text00.txt'

переименован 'dir19/text01.txt' -&gt; 'dir17/text01.txt'

переименован 'dir19/text02.txt' -&gt; 'dir17/text02.txt'

переименован 'dir19/text03.txt' -&gt; 'dir17/text03.txt'

переименован 'dir19/text40.txt' -&gt; 'dir17/text40.txt'

переименован 'dir19/text41.txt' -&gt; 'dir17/text41.txt'

переименован 'dir19/text42.txt' -&gt; 'dir17/text42.txt'

debtop@DebTop:~/playpen$ ls

dir00  dir04  dir08  dir12  dir17  dir21  dir25  dir29  dir33  dir37  dir41

dir01  dir05  dir09  dir13  dir18  dir22  dir26  dir30  dir34  dir38  dir42

dir02  dir06  dir10  dir14  dir19  dir23  dir27  dir31  dir35  dir39

dir03  dir07  dir11  dir15  dir20  dir24  dir28  dir32  dir36  dir40

debtop@DebTop:~/playpen$ ls dir19

debtop@DebTop:~/playpen$ ls dir17

dir         text05.txt  text11.txt  text17.txt  text23.txt  text29.txt  text35.txt  text41.txt

text00.txt  text06.txt  text12.txt  text18.txt  text24.txt  text30.txt  text36.txt  text42.txt

text01.txt  text07.txt  text13.txt  text19.txt  text25.txt  text31.txt  text37.txt

text02.txt  text08.txt  text14.txt  text20.txt  text26.txt  text32.txt  text38.txt

text03.txt  text09.txt  text15.txt  text21.txt  text27.txt  text33.txt  text39.txt

text04.txt  text10.txt  text16.txt  text22.txt  text28.txt  text34.txt  text40.txt
```
_Можно также создать папку с большой вложенностью dir18 и переместить только файлы первого уровня в папку dir19:_

**find dir18/ -maxdepth 1 -type f -print0 | xargs -0 mv -t dir19**

Данная команда находит (find) все файлы (-type f) с глубиной вложенности 1 (-maxdepth 1) внутри dir18 и переместит их в dir19 как обычные файлы (mv -t). Часть «xargs -0» служит в роли команды, связующей две других и позволяет им работать вместе. 

_С глубиной вложенности -maxdepth можно экспериментировать, задавать ей разные значения (1, 2, 3 и т.д.) получая новый результат каждый раз._
## 4. Команды для архивирования
### 4.1. gzip — создание архива. 
Работает следующим образом: gzip файл.расширение. 
Можно создать сразу несколько, например, **gzip text12.txt text13.txt**.
 ```  
debtop@DebTop:~/playpen$ cd dir00

debtop@DebTop:~/playpen/dir00$ gzip text14.txt

debtop@DebTop:~/playpen/dir00$ ls

text00.txt  text07.txt  text14.txt.gz  text21.txt  text28.txt  text35.txt  text42.txt

text01.txt  text08.txt  text15.txt     text22.txt  text29.txt  text36.txt

text02.txt  text09.txt  text16.txt     text23.txt  text30.txt  text37.txt

text03.txt  text10.txt  text17.txt     text24.txt  text31.txt  text38.txt

text04.txt  text11.txt  text18.txt     text25.txt  text32.txt  text39.txt

text05.txt  text12.txt  text19.txt     text26.txt  text33.txt  text40.txt

text06.txt  text13.txt  text20.txt     text27.txt  text34.txt  text41.txt
```
### 4.2. gunzip — распаковать архив 
Работает как gunzip файл.расширение.gz.
``` 
debtop@DebTop:~/playpen/dir00$ ls
 
text00.txt  text07.txt  text14.txt.gz  text21.txt  text28.txt  text35.txt  text42.txt
 
text01.txt  text08.txt  text15.txt     text22.txt  text29.txt  text36.txt
 
text02.txt  text09.txt  text16.txt     text23.txt  text30.txt  text37.txt
 
text03.txt  text10.txt  text17.txt     text24.txt  text31.txt  text38.txt
 
text04.txt  text11.txt  text18.txt     text25.txt  text32.txt  text39.txt
 
text05.txt  text12.txt  text19.txt     text26.txt  text33.txt  text40.txt
 
text06.txt  text13.txt  text20.txt     text27.txt  text34.txt  text41.txt
 
debtop@DebTop:~/playpen/dir00$ gunzip text14.txt.gz

debtop@DebTop:~/playpen/dir00$ ls
 
text00.txt  text06.txt  text12.txt  text18.txt  text24.txt  text30.txt  text36.txt  text42.txt
 
text01.txt  text07.txt  text13.txt  text19.txt  text25.txt  text31.txt  text37.txt
 
text02.txt  text08.txt  text14.txt  text20.txt  text26.txt  text32.txt  text38.txt
 
text03.txt  text09.txt  text15.txt  text21.txt  text27.txt  text33.txt  text39.txt
 
text04.txt  text10.txt  text16.txt  text22.txt  text28.txt  text34.txt  text40.txt
 
text05.txt  text11.txt  text17.txt  text23.txt  text29.txt  text35.txt  text41.txt
```
### 4.3. zip —  для передачи файла на другую операционную систему.
Утилита zip терминала Linux позволяет упаковать сразу несколько файлов в один архив с помощью рекурсивной опции **-r**. Текст команды Linux:

**zip -r texts.zip text12.txt text13.txt**

_В данном случае **texts.zip** будет названием архива, а **text12.txt** и **text13.txt** — файлы, которые нужно поместить в архив._
_**gzip ** также позволяет поместить несколько файлов в архив, но с ней сложнее разобраться_
```
debtop@DebTop:~/playpen/dir00$ zip -r texts.zip text12.txt text13.txt

 adding: text12.txt (stored 0%)

 adding: text13.txt (stored 0%)

debtop@DebTop:~/playpen/dir00$ ls

text00.txt  text06.txt  text12.txt  text18.txt  text24.txt  text30.txt  text36.txt  text42.txt

text01.txt  text07.txt  text13.txt  text19.txt  text25.txt  text31.txt  text37.txt  texts.zip

text02.txt  text08.txt  text14.txt  text20.txt  text26.txt  text32.txt  text38.txt

text03.txt  text09.txt  text15.txt  text21.txt  text27.txt  text33.txt  text39.txt

text04.txt  text10.txt  text16.txt  text22.txt  text28.txt  text34.txt  text40.txt

text05.txt  text11.txt  text17.txt  text23.txt  text29.txt  text35.txt  text41.txt
```
_**gzip ** также позволяет поместить несколько файлов в архив, но с ней сложнее разобраться_
### 4.4. tar — создание резервных копий. 
Утилита **tar** создает архивы с расширением **.tar**, используется для резервного копирования (не сжимает файлы, а только собирает в архив). Чтобы создать архив .tar, выполняется команда с опциями **—cvf**. 

Например:
**tar -cvf newark.tar text07.txt ../dir22**
Создаст архив с именем newark.tar, в который будут помещены файл text.07.txt и все файлы из каталога dir22, располагающегося внутри родительского каталога.

Для просмотра содержимого .tar архива используются опции **-tvf**:

**tar -tvf newark.tar**
```
debtop@DebTop:~/playpen/dir00$ tar -cvf newark.tar text07.txt ../dir22 

text07.txt

tar: Удаляется начальный `../' из имен объектов

../dir22/

../dir22/text04.txt

tar: Удаляются начальные `../' из целей жестких ссылок

../dir22/text07.txt

../dir22/text40.txt

../dir22/text08.txt

../dir22/text32.txt

../dir22/text28.txt

../dir22/text26.txt

../dir22/text11.txt

../dir22/text25.txt

debtop@DebTop:~/playpen/dir00$ tar -tvf newark.tar

-rw-r--r-- debtop/debtop     0 2020-11-25 13:44 text07.txt

drwxr-xr-x debtop/debtop     0 2020-11-25 13:44 dir22/

-rw-r--r-- debtop/debtop     0 2020-11-25 13:44 dir22/text04.txt

-rw-r--r-- debtop/debtop     0 2020-11-25 13:44 dir22/text07.txt

-rw-r--r-- debtop/debtop     0 2020-11-25 13:44 dir22/text40.txt

-rw-r--r-- debtop/debtop     0 2020-11-25 13:44 dir22/text08.txt

-rw-r--r-- debtop/debtop     0 2020-11-25 13:44 dir22/text32.txt

-rw-r--r-- debtop/debtop     0 2020-11-25 13:44 dir22/text28.txt

-rw-r--r-- debtop/debtop     0 2020-11-25 13:44 dir22/text26.txt

-rw-r--r-- debtop/debtop     0 2020-11-25 13:44 dir22/text11.txt

-rw-r--r-- debtop/debtop     0 2020-11-25 13:44 dir22/text25.txt
```
Опции для распаковки **.tar архива -xvf: tar -xvf newark.tar**
```   
-rw-r--r-- debtop/debtop     0 2020-11-25 13:44 dir22/text27.txt

-rw-r--r-- debtop/debtop     0 2020-11-25 13:44 dir22/text39.txt

hrw-r--r-- debtop/debtop     0 2020-11-25 13:44 text07.txt ссылка на text07.txt

debtop@DebTop:~/playpen/dir00$ ls

arch.tar    text05.txt  text11.txt  text17.txt  text23.txt  newark.tar  text35.txt  text41.txt

dir00       text06.txt  text12.txt  text18.txt  text24.txt  scrolls.tar text36.txt  text42.txt

text01.txt  text07.txt  text13.txt  text19.txt  text25.txt  text31.txt  text37.txt  

text02.txt  text08.txt  text14.txt  text20.txt  text26.txt  text32.txt  text38.txt

text03.txt  text09.txt  text15.txt  text21.txt  text27.txt  text33.txt  text39.txt

text04.txt  text10.txt  text16.txt  text22.txt  text28.txt  text34.txt  text40.txt  texts.zip
```
_После выполнения в текущий каталог будут скопированы все файлы из архива, но архив не будет удален. Удалить его можно, выполнив **rm.**_
## 5. Команды для работы с текстом
### 5.1. Nano — редактирование текстовых файлов
Используется для просмотра и редактирования текстовых файлов. 
_Пример: переход в директорию **dir42** и открытие **text42.txt** с помощью Nano._

_**nano text42.txt**_

Записывается текст в файле, затем сохраняется  сочетанием **Ctrl+O** и последующий выход сочетанием **Ctrl+X**.  
Позволяет редактировать файлы прямо из окна терминала.

_Также может быть использован **Vim** (опционально) с более обширными возможностями редактирования.
Для выхода из Vim используется **:q**, для выхода без сохранения изменений — **:q!** и **:w** для сохранения всех изменений. Обязательно сначала использовать двоеточие, так как оно активирует командный режим._
### 5.2. grep — поиск
Для поиска текста в файле используется **grep**- команда выводит соответствующие запросу строки текста. Поиск может быть проивзеден словом, строкой или регулярным выражением, а вывод может быть файлом или папкой, совпадающим или наоборот — несовпадающим. Полезно использовать grep при поиске по большим логам.

_Кроме grep есть варианты **pgrep**, **fgrep**, **egrep**, которые выполняют ту же функцию, но для других целей._

### 5.3. head, tail — начало и конец текста
Команды head и tail используются для вывода первых и последних строк текста в одном или нескольких документах:

**head/tail опции файл**

По умолчанию команды выводят 10 строк текста, но количество можно изменить с помощью опции **-n.**:

``` 
head -n 1 text00.txt

tail -n 1 text00.txt

debtop@DebTop:~/playpen/dir00$ head -n 1 text00.txt

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla ut lacus ut justo blandit mattis

. Sed magna elit, pharetra ac nulla eu, vulputate elementum ex. Donec porta sapien at dui males

uada, quis pretium neque volutpat. Aliquam a tincidunt mi. Nunc posuere vehicula velit, sed int

erdum lorem ullamcorper at. Aliquam finibus ultrices metus pharetra elementum. Aliquam erat vol

utpat. In sit amet sapien commodo dolor feugiat sodales at vitae turpis. Donec ullamcorper dolo

r quis lacus tempor, ac aliquet sem consectetur. Duis nec dignissim ligula. Sed gravida sed arc

u quis commodo. Aliquam vestibulum nunc sed viverra imperdiet. Suspendisse accumsan sollicitudi

n ex, interdum facilisis eros efficitur non.

debtop@DebTop:~/playpen/dir00$ tail -n 1 text00.txt

Aenean non ullamcorper diam. Ut iaculis vehicula libero sit amet elementum. Nullam ipsum metus,

molestie vehicula dui in, tempus finibus nisl. In hac habitasse platea dictumst. In vehicula v

elit nec massa porttitor finibus. Nulla libero justo, egestas vitae fringilla ut, gravida eu ri

sus. Ut eget risus erat. Aenean interdum pretium semper. Aliquam vehicula dolor non augue lacin

ia sodales. Morbi molestie massa sed enim placerat, id euismod odio condimentum. Nunc aliquet l

acinia lacus, quis mattis tortor viverra sed. Vestibulum ullamcorper aliquet nibh, nec lacinia

nunc tincidunt fringilla. Mauris sollicitudin nec lectus eget mollis. Aliquam eu accumsan nulla.
```
С помощью опции **-c** можно запросить уже не строки, а байты.

Например, команды для получения 100 байт текста:

**head -с 100 text00.txt**
```  
debtop@DebTop:~/playpen/dir00$ tail -c 100 text00.txt

ia nunc tincidunt fringilla. Mauris sollicitudin nec lectus eget mollis. Aliquam eu accumsan nulla.

debtop@DebTop:~/playpen/dir00$ head -c 100 text00.txt     

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla ut lacus ut justo blandit mattis. Sed

tail -с 100 text00.txt
```
Другие опции можно посмотреть через **man head**.
```  
HEAD(1)                                 User Commands                                HEAD(1)

NAME
      head - output the first part of files

SYNOPSIS
      head [OPTION]... [FILE]...

DESCRIPTION
     Print  the  first 10 lines of each FILE to standard output.  With more than one FILE,
      precede each with a header giving the file name.

      With no FILE, or when FILE is -, read standard input.

      Mandatory arguments to long options are mandatory for short options too.

      -c, --bytes=[-]NUM
             print the first NUM bytes of each file; with the leading '-',  print  all  but
             the last NUM bytes of each file

      -n, --lines=[-]NUM
             print the first NUM lines instead of the first 10; with the leading '-', print
             all but the last NUM lines of each file

      -q, --quiet, --silent
             never print headers giving file names

      -v, --verbose
```
## 6. Команды для управления процессами
### 6.1. kill / pkill / killall — завершение процесса
**kill** — завершение процесса по его идентификатору (Process ID);
**pkill** — завершение процесса по его имени;
**killall** — убить все процессы с указанным именем.

_**ps / pgrep** — узнать ID процесса_

 _**PS (Process Status)** выводит на экран информацию о запущенных процессах._ 
 
_Чтобы показать список всех активных процессов, используется **ps axu**._
```    
debtop@DebTop:~/playpen$ top

top - 14:21:22 up 8 days, 21:57,  3 users,  load average: 0,49, 0,66, 0,65

Tasks: 181 total,   1 running, 180 sleeping,   0 stopped,   0 zombie

%Cpu(s):  0,8 us,  0,4 sy,  0,0 ni, 98,7 id,  0,0 wa,  0,0 hi,  0,0 si,  0,0 st

MiB Mem :   7856,4 total,   4009,2 free,   1944,6 used,   1902,6 buff/cache

MiB Swap:   8068,0 total,   7913,4 free,    154,6 used.   5390,8 avail Mem

PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND</b>
                    
 690 root      20   0  309888  34416  16856 S   2,0   0,4   5:46.67 Xorg  
                     
11426 debtop    20   0 1195064  78272  62036 S   1,7   1,0   0:15.55 konsole                   
 
 936 debtop    20   0 2994244  59840  36732 S   1,3   0,7   6:10.33 kwin_x11                   

11586 debtop    20   0 9188248 513296 127392 S   1,0   6,4  14:44.20 chrome                     

11068 debtop    20   0  973096 310508 142424 S   0,3   3,9   2:27.42 chrome                     

11107 debtop    20   0  390416 110176  62368 S   0,3   1,4   0:44.15 chrome                     

11516 debtop    20   0 9177080 384808 114828 S   0,3   4,8   0:58.68 chrome                     

   1 root      20   0  169620   6872   5272 S   0,0   0,1   0:02.15 systemd                    

   2 root      20   0       0      0      0 S   0,0   0,0   0:00.02 kthreadd                   

   3 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 rcu_gp                     

   4 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 rcu_par_gp                 

   6 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 kworker/0:0H-kblockd       

   8 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 mm_percpu_wq               

   9 root      20   0       0      0      0 S   0,0   0,0   0:00.07 ksoftirqd/0                

  10 root      20   0       0      0      0 I   0,0   0,0   0:09.29 rcu_sched                  

  11 root      20   0       0      0      0 I   0,0   0,0   0:00.00 rcu_bh                     

  12 root      rt   0       0      0      0 S   0,0   0,0   0:00.17 migration/0                

  14 root      20   0       0      0      0 S   0,0   0,0   0:00.00 cpuhp/0                    

  15 root      20   0       0      0      0 S   0,0   0,0   0:00.00 cpuhp/1                    

  16 root      rt   0       0      0      0 S   0,0   0,0   0:00.37 migration/1                

  17 root      20   0       0      0      0 S   0,0   0,0   0:00.15 ksoftirqd/1                

  19 root       0 -20       0      0      0 I   0,0   0,0   0:00.00 kworker/1:0H-kblockd
  ```
### 6.2. Поиск нужного процесса:
**top (Table Of Processes)** — обновление активных процессов каждые две секунды. Колонка **PID** указывает на ID процесса, **USER** на пользователя и т.д. 

**atop**, **htop** - отображают не только активные процессы с обновлением в две секунды, но и контроль над загрузкой и т.д. 

**ps axu | grep имя_процесса**. С помощью данной утилиты grep можно найти нужный процесс, если известно его имя.
```
debtop@DebTop:~/playpen$ ps axu | grep bash
 
debtop   11468  0.0  0.0   8316  5192 pts/1    Ss   13:20   0:00 /bin/bash
 
debtop   14232  0.0  0.0   6224   888 pts/1    S+   14:22   0:00 grep bash
```
**pidof** — самый короткий способ выяснить ID процесса, если известно его имя.
``` 
debtop@DebTop:~/playpen$ pidof bash
 
11468
```
## 7. Работа с пакетными менеджерами
### 7.1. dpkg — установка файла с расширением **.deb** (только для систем на Debian).
Это файлы, оптимизированные под дистрибутивы на основе Debian (Debian, Ubuntu и Ubuntu-based, Mint и т.д.).

**dpkg -i package.deb** — установка пакета .deb;

**dpkg —remove package** — удаление пакета.

**dpkg —purge package** - удаление остаточных файлов и папок (dependencies).

### 7.2. apt  — менеджер установки пакетов Debian-based
Пакетный менеджер по умолчанию в Debian и дистрибутивах на основе Debian — apt (Advanced Packaging Tool).

Для установки пакета с помощью apt необходимо ввести команду:

**apt install имя_пакета**

_**apt-get** - более старая версия apt. . Пакетный менеджер apt объединяет сразу несколько прежних команд (**apt-get** и **apt-cache** в **apt install** и **apt search**), а также оптимизирует процесс установки пакетов._
Команда для удаления установленного пакета с помощью apt:

**apt remove имя_пакета**

Для удаления остаточных файлов и папок (dependencies) вместо **remove** используется **purge**:

**apt purge имя_пакета**

Для автоматического удаления всего лишнего из системы используется **apt autoremove** - команда удаляет все файлы и зависимости, которые больше не требуются в системе.

### 7.3. yum — менеджер установки пакетов **Red Hat**

Это пакетный менеджер Red Hat и дистрибутивов на основе Red Hat, например **CentOS**. Менеджер yum (Yellowdog Updater, Modified) использует формат пакетов **rpm** вместо **deb**, но команды используются те-же:

**yum install** для установки пакета;

**yum remove** для удаления;

**yum autoremove** для очистки.

_При удалении пакета менеджер yum по умолчанию всегда сохраняет файлы конфигурации, которые отличаются от изначальных по умолчанию и не имеет команды аналогичной apt purge_. 

### 7.4. pacman — менеджер пакетов **ArchLinux**
Еще один дистрибутив, имеющий свой пакетный менеджер — ArchLinux. Пакеты здесь представляют собой архивы формата **.tar.xz**.

Чтобы установить или удалить пакет с помощью pacman используются опции:

**S** устанавливает пакет ArchLinux;

**Sw** скачивает, но не устанавливает пакет;

**U** для установки пакетов с локального компьютера;

**s** для поиска пакетов;

**u** для обновления установленных пакетов;

**R** для удаления;

**Rn** для удаления резервных копий файлов конфигурации;
**Rs** для удаления зависимостей.

После опции всегда идет имя пакета, т.е.:

**pacman -S имя_пакета**
## 8. Команды управления пользователями
### 8.1. sudo — запуск команд и приложений через терминал в Linux от имени администратора (суперпользователя/root)
Для выполнения команды от имени суперпользователя, нужно ввести перед ней **sudo**. Это позволит выполнять команды от имени суперпользователя до окончания текущей сессии в терминале.

_При необходимости можно переключиться в режим суперпользователя. Для нужно выполнить **su** и ввести пароль, тогда выполнение любых команд по умолчанию будет произведено от имени суперпользователя._
### 8.2. useradd (adduser) / userdel (deluser) / usermod — добавление, удаление, изменение пользователя
С помощью этих команд происходит управление учетными записями пользователей. 

Для добавления пользователя используется **useradd имя_пользователя**.

Пароль для нового пользователя задается командой **passwd имя_пользователя.**

Удаление учетной записи производится командой **userdel имя_пользователя**.

**usermod** позволяет изменять учетные записи пользователей: изменять домашнюю директорию, имя учетной записи, оболочку входа в систему, «срок годности» пароля и т.д.
## 9. Команды выключения и перезагрузки
### 9.1. shutdown — выключение
**shutdown опции время сообщение**

Время — отсрочка выключения. Можно указывать:

в 24-часовом формате когда нужно указать точное время выключения с точностью до минуты **shutdown 10:10**;
в формате **+мин**, например, **shutdown +10** выключит компьютер через 10 минут после выполнения. Команды **shutdown +0** и **shutdown now** выключат компьютер немедленно.
**Сообщение (wall)** — текстовое сообщение, отправляемое пользователям компьютеров в сети при необходимости добавления комментария с причиной выключения. При добавлении сообщения обязательно указывать время.

Некоторые опции:

**H (Halt)** — останавливает все функции процессора, но не выключает компьютер. Halt можно использовать как самостоятельную команду, отдельно от shutdown;

**P** — полное выключение компьютера. Можно использовать как команду poweroff;
## 9.2. r (reboot) — перезагрузка. 
В качестве команды — reboot;
**k** — не производить никаких действий, отправить сообщение;
**c** — отменить запланированное выключение. Можно отменить выключение, только если не было задано время +0 или now.
## 10. Бонусные команды
### 10.1. Двойной символ & (амперсанд)**
Предназначен для выполнения нескольких команд последовательно:
**команда1 && команда2 && команда3**

команда3 выполнится только после успешного исполнения команды2, а команда2 — после команды1.

### 10.2. Вертикальная черта | (pipe)
Вводит результат первой команды в последующую. Например, следующая команда добавит таблицу процессов к команде поиска:

**ps axu | grep имя_процесса**

&& и || можно комбинировать. Например вот так: **команда1 && команда2 || команда3**

### 10.3. Стрелки вверх и вниз на клавиатуре
Помогают осуществлять навигацию по последним командам. Стрелка вверх **(Ctrl+P)** — предыдущая выполненная команда, стрелка вниз **(Ctrl+N)** — следующая.

### 10.4. history — история
При выполенении  **history**, терминал выводит на экран последнюю тысячу команд.

### 10.5. Новая вкладка bash
Не всегда удобно иметь несколько окон. Некоторые терминалы, как и браузеры, дают возможность открыть несколько вкладок сочетанием клавиш **Ctrl+Shift+T**.

### 10.6. Копирование и вставка, прерывание команды
**Ctrl+C** прервет выполнение текущей команды, например таблицы процессов, сбросит текст, введенный в строку. Скопировать текст из bash — **Ctrl+Shift+C**, вставить — **Ctrl+Shift+V** (для MacOS — Command+C и Command+V соответственно).