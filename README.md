# Linux_begin
## Дистрибутив GNU/Linux — общее определение операционных систем, использующих ядро Linux, готовых для конечной установки на пользовательское оборудование.
### Наиболее распространённых дистрибутивы:
- Ubuntu 22.04 "Jammy Jellyfish"
- Debian 10 "Buster"
- Fedora 31
- Linux Mint 19.1 "Tessa"
- Elementary OS 5.0 "Hera"
- Arch Linux
- OpenSUSE 15.1
- Zorin OS 15
- Gentoo Linux 10.1
- OpenMandriva Lx 4.0
- Slackware 15.0

### Модуль 1. Знакомство с командами системой помощи и оболочкой UNIX
- man
- --help
- info

#### man [опции] [раздел] manpage.
Программа предназначена для просмотра страниц руководства (manpages). man присутствует во всех версиях UNIX и является старейшей системой помощи.
Для получения справки о программе, функции, формате файла, в командной строке необходимо набрать man имя_программы.
Документация хранится в специально форматированных текстовых файлах, в директории /usr/share/man.

![Иерархия файловой системы](https://github.com/tvgVita69/Linux_begin/assets/98489171/82618256-a45b-4976-b355-a8e3475b352d)

#### Разделы man.
- man1 Системные утилиты общего пользования
- man2 Функции системы
- man3 Библиотечные функции
- man4 Описание устройств
- man5 Форматы конфигурационных файлов
- man6 Игры
- man7 Различные описания
- man8 Административные утилиты
- man9 Дополнительная документация по ядру

#### Для получения краткой информации о программе, написанной сообществом GNU, следует использовать параметр --help.
Примеры:
- ls --help
- cat --help
  
#### info [menu-item].
Система помощи, разработанная сообществом GNU.
В основном содержит описание программ, созданных GNU сообществом.
Информация хранится в специально отформатированных текстовых файлах.
В отличии от программы man, info позволяет создавать меню и переходы. Система, чем-то напоминает WEB страницы.

#### Документация к программам.
С программами, входящими в дистрибутивы, поставляется документация.
Документация к программам находится в директории /usr/share/doc. В ней находятся директории с именами программ, в которых, собственно, и расположена документация по конкретной программе.

#### Программы-оболочки.
13
Программы-оболочки
–Bourne shell (sh)
- Korn shell (ksh)
- Bourne again shell (bash)*
–C shell (csh)
- TC shell (tcsh)
    
*В Linux стандартной оболочкой по умолчанию является bash

### Модуль 2. Переменные окружения и встроенные команды bash.
- SHELL – содержит путь к shell текущего пользователя
- LS_COLORS – определяет соответствие между расширениями файлов и теми цветами которыми те отражаются в при выводе командой ls
- USER – текущий пользователь
- HOME – домашний каталог пользователя USER
- PATH – содержит пути для поиска файлов по умолчанию
- PWD – указывает на текущий каталог
- LANG – определяет текущие настройки локали
#### Встроенные команды bash.
- env – выводит список переменных окружения
- export – экспортирует переменные окружения, делая их доступными для других программ
- echo – выводит на терминал то, что передано в качестве параметра, в том числе и esc-последовательности*
- reset – возврат настроек терминала к значениям по умолчанию
- logout – завершение текущего пользовательского сеанса
- exit – завершение сеанса работы с оболочкой
   
*традиционным способом управления терминалом является отправка на него esc-последовательностей, для чего echo выполняется с ключами -ne

### Модуль 3. Повышение привилегий до суперпользователя.
В Ubuntu по умолчанию отключена возможность входа в систему для суперпользователя. Для выполнения команд с правами суперпользователя используется команда sudo
   
Пример:   
- sudo su - выполнить команду su, т.е. создать сеанс суперпользователя root
- sudo -i - запустить командную оболочку с правами суперпользователя root. Для выполнения данной команды пользователь должен иметь право на выполнение программы оболочки в среде sudo, например - /bin/bash
##### Другие командыс использованием sudo.
- sudo –l - отобразить список команд, доступных для выполнения текущему пользователю. Кроме списка команд отображаются параметры среды, которые будут применяться при их выполнении.
- sudo –ll - отобразить список команд, доступных для выполнения текущему пользователю в длинном (расширенном) формате.
- sudo lshw -C network - отобразить информацию о сетевом оборудовании с правами суперпользователя root
- sudo –l –U user1 - посмотреть список команд, доступных для выполнения пользователю user1. 
##### Командная строка sudo может быть использована в следующих форматах:
- sudo -h | -K | -k | -V
- sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
- sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user] [command]
- sudo [-AbEHknPS] [-C num] [-g group] [-h host] [-p prompt] [-u user] [VAR=value] [-i|-s] []
- sudo -e [-AknS] [-C num] [-g group] [-h host] [-p prompt] [-u user] file

### Модуль 4. Основные команды.
![Основные команды работы с файлами](https://github.com/tvgVita69/Linux_begin/assets/98489171/d0f35cbf-9b6b-49c0-ba05-752a2e26e428)
#### Примеры использования команд.

- ls -alF /etc
- pwd
- cd /etc
- pwd
- cd ~
- touch test
- ls -l test
- mkdir -p dir1/dir2/dir3
- cp test dir1/dir2
- mv test mytest
- rmdir dir1/dir2/dir3
- cat /etc/passwd
- tac /etc/group
- more /etc/services
- less /etc/rsyslog.conf
- ln mytest test
- ln -s dir1/dir2/test mytest2
- ls -l *test*
- rm mytest
- rm -rf dir1
- ls -l *test*
- rm *test*

#### Перенаправление ввода-вывода и ошибок.
- cat > testfile <br>
Введите строку и нажмите Enter <br>
Нажмите Ctrl+D – (EOF) для завершения работы
- cat testfile > testfile 2> errfile
- cat errfile
- cat /etc/passwd > testfile2
- cat < /etc/group > testfile
- ls -l /etc > mylist
- touch /bin/mycustomfile 2> errfile
- cat errfile

![Дополнительные команды работы с файлами](https://github.com/tvgVita69/Linux_begin/assets/98489171/c8ae620c-f17b-4771-bb2f-434ba7f7550d)

#### Примеры использования дополнительных команд.
- df -h
- du -h /var/log
- ls /etc | sort | less
- ls /etc/*.conf | wc -l
- cat /etc/services | head
- ls -l /etc | tr 'rwx' 'RWX'
- ls -l /etc | tee test | tail
- wc -c test
- dd if=/dev/cdrom of=~/my.iso
- cat | uniq -d
- grep -rsni pppd /usr/share/doc
- cat > test
- line1:the 1st
- line2:the 2nd
- line3:the 3rd
{нажмите Ctrl+D}
- cut -f 1 -d: test > tmp1
- cut -f 2 -d: test > tmp2
- paste tmp2 tmp1 > test
- rm tmp* && cat test






