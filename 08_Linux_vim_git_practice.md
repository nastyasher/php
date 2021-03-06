# Linux, VIM, GIT practice

На данном уроке мы познакомимся с базовыми командами работы в ОС Linux в теории и на практике, затем мы выложим сайт на хостинг A-Level, и в третьей части урока попрактикуемся в навыках работы с контролем версий GIT.

## Linux basics

По выданным вам логинам, паролю и адресу сервера при помощи программы Putty вы попадете в консоль сервера Helium, на котором нам предстоит практиковаться в Linux.

Самые основные команды, которые необходимо знать:

- [ls](https://www.opennet.ru/cgi-bin/opennet/man.cgi?topic=ls&category=1) с различными опциями - просмотр содержимого текущей или указанной папки
- [cd](https://www.computerhope.com/unix/ucd.htm) - команда для смены текущей папки
- [pwd](https://linux.die.net/man/1/pwd) - посмотреть текущую папку
- [passwd](https://www.opennet.ru/man.shtml?topic=passwd&category=1) - сменить пароль
- [mkdir](https://www.opennet.ru/man.shtml?topic=mkdir&category=1&russian=0) - создать папку

Дальше подробнее)

### Команды и основы использования bash

Команды бывают внутренние (их реализует непосредственно программа-оболочка) или же другие программы, существующие в файловой системе.

Клавиатурные комбинации:

__TAB__ - "волшебная" кнопка, которая дополняет ваш текст. Не надо писать всё, надо жать TAB. Иногда два раза.
__CTRL-W__ - стереть слово до курсора
__CTRL-R__ - поиск по истории команд. Достаточно ввести любую часть другой команды что бы её выдернуть для использования сейчас.
__СТРЕЛКА ВВЕРХ__ - история
__Alt-B__ - слово назад.

Команда  выводит историю ваших команд.

### Создание и удаление файлов и директорий. touch, mkdir, rm, ls, cat, ...

Ниже идет джентльменский набор файловых операций, реализуемых командами:

`pwd` - (present working directory) показывает где мы сейчас находимся
`cd` - (change directory) сменить дерикторию
`mkdir` - (make dir) создать дерикторию
`rmdir` - (remove dir) удалить дерикторию
`cp` - (copy) копировать что либо
`mv` - (move) переместить что либо
`rm` - (remove) - удалить


#### Туда и обратно
```
cd ~/tmp # change directory: зайти в папку tmp в домашней папке текущего пользователя
cd       # идем в домашнюю папку
cd ./    # зайти в эту же папку
cd ../   # выйти на папку выше.

```

#### А есть че?
```
ls -la   # list подробно и с правами
ls       # list неподробно
ls -lah  # list подробно и с понятными размерами файлов

```

### Wildcard
Вы можете использовать символ `*` для замены части имени файла на любые:
`ls -la *php # показать все файлы php в директории`

При этом команда `ls` получит в качестве параметров **все файлы в папке, которые оканчиваются на php**.


#### Я хочу создать!

```

touch filename           # создает пустой файл filename, или обновляет время доступа к файлу ("касается" его)
mkdir ~/newFolder        # создаем папку в домашнем каталоге
mkdir newFolder          # создаем папку в текущем каталоге
mkdir ../newFolder       # создаем папку рядом с текущим (т. е. на уровень выше)
mkdir -p ~/newFolder/1/2/3/4/5/6 # создадим сразу несколько папок друг в друге

```

#### Переименовать или перенести:

```
mv ~/newFolder/1/2/3/4/5/6 ~/newFolder # перенесем папку 6 из папки 5 в папку ~/newFolder
mv filename otherFilename              # переименуем файл в другое имя файла.
```

#### Копировать

```
cp otherFilename filename             # копируем один файл из otherFilename в filename
cp -vrf ~/newFolder/1/2/ ~/newFolder  # copy verbose recursive force папку ~/newFolder/1/2 в ~/newFolder

```

![delete](https://cs6.pikabu.ru/images/big_size_comm/2017-07_5/1500953595190652479.jpg)

#### Удалить

```
rm otherFilename      # remove file otherFilename
rm -rf ~/newFolder/1  # remove files and directories recursively forced.

```

#### А что в файле?

```
cat /etc/resolv.conf # conCAT /etc/resolv.conf

```

#### Как выйти из Vim или о текстовых редакторах

Все мы в той или иной степени знакомы с редакторами текста. Однако в мире UNIX редакторы изначально более мощные и гибкие, ориентированные на работу с кодом или конфигурационными файлами.

##### `vim`

__ViM__ - (__vi__ i__m__proved) - мощный редактор, который построен не на идее редактирования текста, а на идее программирования редактирования текста. Благодаря этому вы при редактировании оперируете не отдельными символами, а сущностями, имеющими отношение к структуре программного кода (слова, параметры, парные тэги/скобки и так далее)

##### Режимы работы ViM;


* Нормальный. Это режим, в котором собственно происходит программирование текста

![vim keys](http://gitlab.a-level.com.ua/gitgod/Linux/raw/master/vi-vim-cheat-sheet.gif)

Каждая клавиша на клавиатуре в этом режиме отвечает за то или иное действие: перемещение, изменение, удаление, вставку, копирование блока текста и так далее.


##### Выход из ViM

* `Esc:q!` - выйти не сохраняясь
* `Esc:wqa` - выйти, сохранив все файлы
* `ZZ` - выход с сохранением.
* `Esc:x` - эквивалент `Esc:wq`


### Абсолютные и относительные пути, ~ и проч.

Пути бывают абсолютные и относительные, а так же относительно домашней папки(`/home/username`). Для этого используется следующий синтаксис:

`/etc/` - Путь, начинающийся со слеша - абсолютный
`tmp` - Путь без слеша означает путь относительно текущей папки. Иногда надо поставить ./ перед именем папки или файла (./tmp)
`~/` - домашняя папка. Обычно /home/username.
`~username` - домашняя папка пользователя.
`.., ../` - папка уровнем выше
`./` - текущая папка.

Каждый файл или папка в UNIX ОС имеют права доступа, которые побиты на 3 восьмеричных цифры (3 бита x 3 блока).

##### Права доступа

	- `r`- read
	- `w`- write
	- `x` -  eXecute/доступ к папке

Каждый из этих трех прав доступа назначаются:

* Владельцу
* Группе
* Остальным.
Для задания владельца используется команда __chown__ (__CH__ange __OWN__er):

```
chown username filename # меняем владельца
chown -R username:groupname ~/newFolder # меняем владельца и группу для папки ~/newFolder рекурсивно
```

Для задания прав доступа используется команда chmod

```
chmod 700 filename # полный доступ для владельца, ноль доступа группе и остальным
chmod -R a+x ~/newFolder # добавить всем доступ на запуск всем (владельцу, группе, и остальным) рекурсивно
```

## Hard & symlinks. 

В файловой системе есть ссылки двух типов - текстовые файлы с путем к другим файлам. Это симлинки. 
А так же есть копии файловых записей, которые ссылаются на контент файлов. Это хардлинки

Первые работают в разных файловых системах, однако если файл, на который сделана ссылка удалится - ссылка станет битая
Вторые работают только в одной файловой системе, однако все ссылки на контент файла **равноправны** и файловая система
ведет подсчет этих ссылок, освобождая место только после удаления **последней** ссылки.

для работы с этими ссылками используется команда `ln`.


##### Root

![root](https://sophosnews.files.wordpress.com/2016/11/root-1200.png?w=780&h=408&crop=1)

Так как Линукс это многопользовательская ОС то и должны быть определенные ограничения для пользователей

Таким ограничением являеться отстуствием прав root.

__root__ это кроме как корень еще и пользователь системы

Пользователю __root__ позволено все: удалять, копировать или записывать или запускать любой файл которые находиться в системе

Пользователь __root__ имеет наивысшие привелегии на все.

То есть __root__ это полноценный администратор машины(компьютера).

Если вам надо установить программу или поправить конфигурации вам нужно зайти под этим пользователем в систему.

Но это __НЕ РЕКОМЕНДУЕТСЯ!!!__

*Сидеть под рутом* отчасти опасно так как вы можете случайно сделать что то не то и вы можете попращаться с системой. 

##### Выход есть!

[__sudo__](https://ru.wikipedia.org/wiki/Sudo) -- *substitute user and do*, дословно «подменить пользователя и выполнить»

Специальная программа которая позволяет запускать небольшие сессии под рутом от обычного пользователя что бы улучшить общее состояние безопасности и дать вам второй шанс если вы вдруг чего то недосмотрели

Для того что бы иметь такие права вам все равно придется раз зайти под рутом

Правила, используемые __sudo__ для принятия решения о предоставлении доступа, находятся в файле `/etc/sudoers` (для редактирования файла можно использовать специальный редактор visudo, запускаемый из командной строки без параметров, в том числе без указания пути к файлу); язык их написания и примеры использования подробно изложены в man sudoers(5).

## Итог

В bash и других линуксовых консолях существует множество интересных команд, и еще большее количество вариантов их использования, каждый интересующийся пользователь постепенно узнает для себя интересные команды и их варианты.

Для заинтересованных данной темой рекомендуем ознакомиться с возможностями командной строки в целом, так как сложно представить себе более мощный инструмент для программиста и системного администратора.

#### Полезные сслыки

[Командная строка](http://web-old.archive.org/web/20161202141902/http://www.ibm.com/developerworks/ru/library/l-lpic1-v3-103-1/index.html)

[Необычные решения сложных задач одной строкой](http://www.bashoneliners.com/oneliners/popular/)

[О bash](https://ru.wikipedia.org/wiki/Bash).

[Домашнее задание](08_homework.md)

[Следующий Урок](09_web_basics.md)
