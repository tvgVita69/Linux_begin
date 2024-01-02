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

### Модуль 4. Управление правами доступа.
Система безопасности UNIX построена на определении прав доступа к файлам.
- chmod — изменение прав доступа
- umask — маска прав доступа
- chown — изменение хозяина
- chgrp — изменение группы

### Модуль 5. Типы файлов.
Тип файла можно определить по первой <br>
букве вывода программы ls -l. <br>
- f или - — обыкновенный файл
- l — символьная ссылка
- d — директория
- c — символьное устройство
- b — блочное устройство
- p — pipe (FIFO) файл
- s — файл типа socket
   
![Система беопастности](https://github.com/tvgVita69/Linux_begin/assets/98489171/b23a31f0-b73c-48b3-a626-c4e035246740)
#### Типы прав доступа к файлам.
- r — право на чтение из файла
- w — право на запись в файл
- x — право на исполнение
#### Интерпретация прав доступа к каталогам.
- r — право на просмотр содержимого директории
- w — право на создание, удаление файлов в директории
- x — право на «прохождение» в и сквозь директорию

#### Числовой формат записи прав.
![image](https://github.com/tvgVita69/Linux_begin/assets/98489171/922aecbe-c18e-48db-bd4b-dfd2d3ec73ec)
#### Символьный формат записи прав.
![image](https://github.com/tvgVita69/Linux_begin/assets/98489171/6ed0b22e-59fc-4db4-ab5d-e6e803e01db8)
#### Специальные права.
![image](https://github.com/tvgVita69/Linux_begin/assets/98489171/6635fd97-90c9-4629-b7e1-ed1a30a35ca9)
#### Права доступа по умолчанию.
- Для директорий — 777
- Для файлов — 666
### Модуль 6. Основные команды.
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
### Модуль 7. Файлы Linux. 
чтобы определить, какая файловаяw система на разделе /dev/sda1, наберите команду file с ключом -s:

sudo file -s /dev/sda1

# df -T - показывает тип файловой системы.
# df -Th
df -h отображает информацию о смонтированных разделах с отображением общего, доступного и используемого пространства
/dev/sda1 
sd [abcd] [12345] – диск – экземпляр – раздел
Дисковое пространство принимается за 110%
du /var - подсчитывает и выводит размер, занимаемый директорией
du -h -s /var 2>/dev/null
du --max-depth=1 /usr/share/


# ls
отобразить содержимое указанной директории
pwd
.имяфайла - скрытые файлы
Какими командами вывести сведения, когда создавался, менялся, был прочитан файл:
ls -l --time=ctime testfile - когда создавался, менялся
ls -l --time=atime testfile - когда был прочитан
- регулярные файлы
d – директории
Каталоги
pwd - показать текущую директорию
drwxr-xr-x	 .  –текущий каталог
drwxr-xr-x	 . . – родительский каталог
ls -l ..
Переходы между директориями:
cd .. перейти в директорию уровнем выше 
cd ../.. перейти в директорию двумя уровнями выше 
cd перейти в домашнюю директорию 
cd ~user перейти в домашнюю директорию пользователя user 
cd - перейти в директорию, в которой находились до перехода в текущую директорию
cd /user/user1
cd /../../bin/bash
ls -a ~ 	(~ - домашний каталог)
id
whoami
mkdir
ls -l
rm – файла
rm -r удаление не пустого каталога
rmdir – пустого каталога
cp что куда
cp /etc/passwd .
ls
mv что куда
Переименование 
Перемещение 
перемещение под другим именем.

Создание ссылок в Linux 
# ln файл ссылка
# ln file1 file2
Символьную ссылку можно создать при помощи команды ln с ключом -s (от "symbolic"). Например:
ln -s /root/lnfile1 /var/softlfile1
Поиск всех жестких ссылок файла (по inode)
touch file1
ln file1 /var/file2
ls -li
5644346 -rw-r--r-- 2 root root    0 Sep 27 21:39 file1   
find / -inum 5644346 2>/dev/null
Программы поиска файлов:
which – показывает путь к каталогу указанного файла
which vi
locate -  позв. найти файл, указанный по имени
locate hello
cat (concatenation, firstly, In pair with split command)
сегодня используется для вывода на экран содержимого файла
tac file1 -вывести содержимое файла file1 на стандартное устройство вывода в обратном порядке (последняя строка становиться первой и т.д.)
Пример создания и заполнения файла командой cat:
~# cat > file1
12345
^C
~# cat >> file1
23456
^C
~# cat file1
~# tac file1

split разбивала файл на дискеты по 1440, cat потом собирала файл:
 Пример:
# dd if=/dev/zero of=bigfile1 bs=1024 count=20000
$ split -a 1 -d -b 2M bigfile1 bigfile1.part
# rm bigfile1
$ cat bigfile1.part* > bigfile1.iso
# rm  bigfile1.part*

more  - скроллинг только вниз
more /etc/passwd
less - скроллинг вверх и вниз, PgUp / PgDwn работает
 Например, man форматирует для вывода на устройство, а less выводит
 Выход из команды: q
Для просмотра логов - tail. По умоnчанию, выводит 10 последних строк. Можно переопределить параметром –n.
tail -n 20 /var/log/auth.log
tail -f -n 0 /var/log/auth.log
выводим на экран 0 старых записей (-n 0) и ждем появления для отображения новых (-f).
Для разделения результатов вывода м. исп. ================= “Enter”
Для выхода исп. Ctrl + C – сигнал «завершить работу»
Противоположно предыдущей команде, head выводит начало файла.
Работа с историей команд (history)
Ctrl + r – шаблон поиска – поиск по истории
для просмотра списка ранее введенных команд в bash — имеется команда history. По умолчанию все пишиться в файл ~/.bash_history, а его размер — 500 команд.

Если хотим хранить историю в другом файле, то нужно в .bashrc, задать команду HISTFILE=~/.my_history.
HISTSIZE — определяет число строк, хранящихся в списке истории (в памяти интерпретатора).
HISTFILESIZE — максимальное количество команд хранящихся в файле 
$ export HISTSIZE=1000
$ export HISTFILESIZE=1000
возможность указать
количество выводимых строк (команд):
$ history 20
все команды имеют номер, с помощью которого к ней можно обратится.
Если нам надо повторить 28 команду, то просто набираем в терминале:
$ !28
Cписок наиболее распространенных команд:
!! — ссылается на предыдущую команду; 
!n — ссылается на команду под номером n; 
!-n — ссылается на команду по номером „текущая минус n“; 
history -c — очистить историю команд, удалив все записи 
history -d n — удалить из истории запись под номером n 
history -a — дописать команды, введенные в текущей сессии bash, в конец файла $HISTFILE 

Так же можно сохранить дату и время для каждой команды в истории, для этого в конец .bashrc дописываем:
$ nano .bashrc
Для начала найдём где есть файл .bashrc
# find / -name .bashrc
# /root/.bashrc
#/home/user/.bashrc
Дописываем строку в конец файла  .bashrc дописываем
export HISTTIMEFORMAT=" %h/%d-%H:%M:%S  "
Перезагружаем скрипт .bashrc
# . ~/.bashrc
Или
# source ~/.bashrc


 
МОД. 3. РЕГУЛЯРНЫЕ ВЫРАЖЕНИЯ. РЕДАКТОРЫ.
Регулярные выражения
# man re_format

Общая схема регулярного выражения
регулярное выражение состоит из трёх основных частей:
1.	Якорь – определяет позицию шаблона в строке текста: 
o	^ – якорь, определяющий начало строки;
o	$ – якорь, определяющий конец строки.
2.	Шаблон - набор (последовательность) символов – для поиска соответствий в заданных позициях строки текста: 
o	символ "точка" (.) соответствует любому произвольному символу;
o	алфавитно-цифровые символы и пробел представляют сами себя;
o	прочие символы – интерпретация зависит от диалекта.
3.	Модификатор – задаёт количество повторов предыдущего символа или набора символов (в зависимости от диалекта): 
o	* – любое количество повторов символа/набора, в том числе и нулевое;
o	? – соответствует нулю или одному экземпляру символа/набора;

Символы базовых регулярных выражений:
^ - соответствует началу строки;
Пример: grep '^s' /etc/passwd
 $ - соответствует концу строки;
Пример: grep 'sh$' /etc/passwd
 [] - любой символ из числа заключенных в скобки (символы могут быть разделены запятыми, указание диапазона - [0-9]); 
Пример: [012345789] – соответствует одному цифровому символу из заданного набора;
Предназначены для задания подмножества символов. Квадратные скобки, внутри регулярного выражения, считаются одним символом, который может принимать значения, перечисленные внутри этих скобок. Метасимвол ^ означает отрицание множества:
 [^] - любой символ кроме тех что указаны в скобках;
Пример: grep '^[rs]' /etc/passwd
 \ - Служит для экранирования специальных символов, т.е. отменяет спец. значение следующего за ним метасимвола;
Пример: grep 'bin\/sh' /etc/passwd
-- \<...\> --  Экранированные "угловые скобки" - задают границы слова (не работает в sed).
Пример: grep -R '\<sed\>' /usr/share
 . - Означает не менее одного любого символа;
 * - Означает любое количество символа в строке, предшествующего «звездочке», в том числе и нулевое число символов;
Например, имеется шаблон для поиска любого количества символов, заключённых в кавычки:
".*"
-- \( \) --Экранированные "круглые скобки" 
Предназначены для выделения групп регулярных выражений. Они полезны при использовании с оператором «\|» и при извлечении подстроки. 

-- \{ \} -- Экранированные "фигурные скобки"
Задают число вхождений предыдущего выражения. Для уточнения количества повторений наборов символов применяется модификатор \{min,max\}.
Пример: grep '\(ro.*\)\{2\}' /etc/passwd
Пример: ip a | grep '[1-9][0-9]\{0,2\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}'
Зная, что в каждой части IP-адреса может содержаться от одной до трёх цифр, запишем модификатор в виде \{1,3\}. Символы "обратный слэш" перед точками необходимы для того, чтобы отменить их специальный статус универсального метасимвола.
 \{n\} - указывает на то что предыдущий шаблон встречается ровно n раз;
 \{n,\} - указывает на то что предыдущий шаблон встречается не менее n раз;
 \{,m\} - указывает на то что предыдущий шаблон встречается не более m раз;
 \{n,m\} - указывает на то что предыдущий шаблон встречается не менее n раз и не более m раз;
n|m - выбор из двух шаблонов
 \> - признак конца слова;

Классы символов:
 [:upper:] - [A-Z];
 [:lower:] - [a-z];
 [:digit:] - [0-9];
 [:alnum:] - [0-9a-zA-Z];
 [:space:] - символ пробела;
 [:alpha:] - [A-Za-z];
Пример: # grep [[:upper:]] /etc/passwd

*grep [параметры] регулярное_выражение [файл]
-c - задает отображение только числового значения, сколько строк соответствует шаблону;
-i - игнорировать регистр;
-h - подавляет вывод имен файлов, включающих найденные строки;
-l - только отображение имен файлов, содержащих найденные строки;
-n - нумерация выводимых строк;
-s - подавляет вывод сообщений о несуществующих или нетекстовых файлах и ошибках;
-v - отображение строк, не соответствующих шаблону;
-E - включение расширенных регулярных выражений;
POSIX делит регулярные выражения на две категории: 
BRE (Basic Regular Expressions) и ERE (Extended Regular Expressions). 
В обеих категориях поддерживаются метасимволы . и *, якоря ^ и $, группирование символов в скобках (для BRE скобки экранируются обратным слэшем), применение квантификаторов \{min,max\} к группам в скобках. Запоминание и повторное использование \1...\9 поддерживает только категория BRE, а квантификаторы + и ? и конструкцию выбора – только категория ERE.
Символы расширенных регулярных выражений
Многие символы, экранируемые в базовых выражениях – () {} | – но не – <> – используются без экранирования. 
Знак вопроса -- ? --
Означает, что предыдущий символ или регулярное выражение встречается 0 или 1 раз. 
$ grep -E '^r?o' /etc/passwd
Знак "плюс" -- + --
Указывает на то, что предыдущий символ или выражение встречается 1 или более раз 



Как вывести из конфига только незакомментированные строки? Использовать рег выражение:
grep '^#' /etc/ssh/sshd_config (спец символы засовываем в  ‘’)
grep '^#' /etc/ssh/sshd_config (^# начинаются с #)
grep -v '^#' /etc/ssh/sshd_config (-v начинаются не с #)
grep -v '^#\|^$' /etc/ssh/sshd_config (при отрицании -v  «и» (оператор «\|» )меняется на «или» , т.е. не содержат пробелы ^$)
Вывести общее кол-во папок в указанной директории:
# ls -l ~ | grep "^d" | wc -l

----------------------------------------------------------------
ПОТОКОВЫЕ РЕДАКТОРЫ

Потоковый редактор sed
Формат команды
sed команды_редактирования [имя_файла] 

-i – редактировать файл
sed -i 's/string1/string2/' example.txt 	в файле example.txt заменить "string1" на "string2", результат вывести на стандартное устройство вывода. 
sed -i '/^$/d' example.txt 	удалить пустые строки из файла example.txt 
sed  -i '/ *#/d; /^$/d' example.txt 	удалить пустые строки и комментарии из файла example.txt 
-e – добавить к команде скрипт
	
sed -e '1d' example.txt	удалить первую строку из файла example.txt 
sed -n '/string1/p' example.txt	отобразить только строки содержащие "string1" 
sed -e 's/ *$//' example.txt 	удалить пустые символы в конце каждой строки 
sed -e 's/string1//g' example.txt 	удалить строку "string1" из текста, не изменяя всего остального 
sed -n '1,8p;5q' /etc/passwd	взять из файла с первой по восьмую строки и из них вывести первые пять 
sed -n '5p;5q' /etc/passwd	вывести пятую строку 
sed -e 's/0*/0/g' /etc/passwd	заменить последовательность из любого количества нулей одним нулём 
____________________________________________________________________________
Еще пример:
# g > output.txt
# sed -e 's/\(.*\)/\U\1/' sshd_config > output.txt  --- запись содержимого файла с большой буквы
# sed -e 's/\(.*\)/\L\1/' sshd_config > output.txt   -- запись содержимого файла с маленькой буквы

УТИЛИТА TR
Команда tr служит для перевода выбранных символов в другие символы или удаления их. tr не принимает имен файлов в качестве аргумента.
echo 'test' | tr '[:lower:]'  '[:upper:]' 	преобразовать символы из нижнего регистра в верхний 
# cat sshd_config | tr '[:lower:]'  '[:upper:]'
P.s. Пробел должен быть между lower и upper. И привязана строка к регистрам.

РЕДАКТОР VI
Vi – есть везде.
vimtutor – встроенный учебник
Cp /etc/passwd ~
Cd
Vi passwd
J - вниз
K – вверх
L – вправо
G – в начало на первый символ
Редактирование текста
Режим вставки 
i	- ввод текста с текущей позиции
o	- ввод текста с новой строки
Командный режим
J	- склеить строки
x	- удалить текст (DEL)
X	- удалить текст (BACKSPACE)
yy	- копировать строку в буфер
dd	- вырезать строку в буфер
p	- вставить строку из буфера под выбранной строкой
P 	- вставить строку из буфера над выбранной строкой
u	- отменить последнее действие

Командный режим – во всем тексте замени значение Х на 1
:%s/X/1/g

Редактирование конфигов
Перед редактированием конфига, его оригинал нужно сохранять
Кроме cp /etc/ssh/sshd_config /etc/ssh/sshd_configXXXXXX
Можно и лучше использовать систему контроля версий (только ее нужно сначала установить 
apt-get install rcs
RCS - это Система Управления Исправлениями (revision control system)
RCS включает в себя следующие программы:
rcs, которая управляет атрибутами архивного файла RCS; 
ci и co, проверяющие старые и измененные архивы RCS; 
ident, которая производит поиск в архивах RCS по ключевому слову; 
rcsclean, программа которая удаляет нерабочие или неизмененные файлы; 
rcsdiff, которая запускает diff для сравнения версий; 
rcsmerge, которая объединяет результаты работы двух пользователей над файлом в один работающий файл; 
rlog, которая выводит сообщения из журнала RCS.

Создать каталог для репозитория
 mkdir RCS
Затем импортировать файл:
 ci testfile
Исходный файл _перемещается_ в репозиторий (если он там уже есть, то под новой версией).
[ci -l  /etc/ssh/sshd_config – запомнить состояние файла.]
Предложит ввести комментарий, если идей нет просто ставим “. “
Извлечь файл из репозитория можно командой:
co testfile
(файл будет иметь права доступа 444)
Чтобы изменить файл, нужно установить его блокировку и установить права доступа, разрешающие запись
rcs -l testfile
chmod o+w testfile
cat >> testfile
23232323
Правим файл, смотрим рез:
# rcsdiff testfile – смотрим, что (на что) поменялось.
Строка - измененная строка (1a2)
1a2 – первой добавилась вторая
> 23232323 – что добавилось (операция)
Чтобы записать изменения нужно снова выполнить
ci testfile
# rlog ./testfile – сколько и какие версии и ревизии версий
что поменялось относительно указанной версии:
# co testfile
# rcsdiff  -r1.1 testfile

что поменялось между указанными версиями:
rcsdiff  -r1.1  -r1.2  testfile

Мод. 4. Процессы
Упр сервисами и процессами:

# Ps
ps aux - отобразить все существующие процессы.
ps a  -все интерактивные процессы.
ps ax -все процессы.

# pstree – выводит дерево процессов
Каждый запущенный процесс в любой момент времени находится в одном из следующих состояний (статусов):
•	Активен (R=Running) – процесс находится в очереди на выполнение, то есть либо выполняется в данный момент, либо ожидает выделения ему очередного кванта времени центрального процессора.
•	«Спит» (S=Sleeping) – процесс находится в состоянии прерываемого ожидания, то есть ожидает какого-то события, сигнала или освобождения нужного ресурса.
•	Находится в состоянии непрерываемого ожидания (D=Direct) – процесс ожидает определенного («прямого») сигнала от аппаратной части и не реагирует на другие сигналы;
•	Приостановлен (T) – процесс находится в режиме трассировки (обычно такое состояние возникает при отладке программ).
•	«Зомби» (Z=Zombie) – это процесс, выполнение которого завершилось, но относящиеся к нему структуры ядра по каким-то причинам не освобождены.
Потоки данных
У каждой программы существует 3 системных потока: stdout, stderr, stdin
Linux предоставляет специальные команды для перенаправления каждого потока
Команды с одной угловой скобкой переписывают существующий контент целевого файла:
•> — стандартный вывод
•< — стандартный ввод
•2> — стандартная ошибка

Команды с двойными угловыми скобками не переписывают содержимое целевого файла:
•>> — стандартный вывод
•<< — стандартный ввод
•2>> — стандартная ошибка
Можно создать каналы (pipes). между двумя процессами, в который один процесс сможет писать поток байтов, а другой процесс сможет его читать. 
При помощи каналов организуются конвейеры оболочки. Когда оболочка видит строку вроде
команда1 | команда2
Переменные окружения.
Пример: 
date
unset LANG ##отменить унаследованную переменную
date
export LANG=ru_RU.UTF-8 ##вернуть значение взад. Экспортировать потомкам
date
СИГНАЛЫ.
сигналы позволяют управлять программным обеспечением
отличие сигналов от других средств взаимодействия между процессами заключается в том, что их обработка программой обычно происходит сразу же после поступления сигнала (или не происходит вообще), независимо от того, что программа делает в данный момент. Сигнал прерывает нормальный порядок выполнения инструкций в программе и передает управление специальной функции – обработчику сигнала.
SIGHUP (номер 1) изначально был предназначен для того, чтобы информировать программу о потере связи с управляющим терминалом (терминалы часто подключались к системе с помощью модемов, так что название сигнала происходит от hung up – повесить трубку). В ответ на получение SIGHUP демон обычно перезапускается (или просто повторно читает файл конфигурации).

Например, поменяли порт в /etc/ssh/sshd_conf- (sed -i 's/22/222/' /etc/ssh/sshd_config) сделали
ps aux | grep user1
kill -s HUP <PID>
или
kill -HUP <PID>
оно же
kill -1 <PID>
и не надо перезагрузки сервиса.

SIGINT (номер 2) обычно посылается процессу, если пользователь терминала дал команду прервать процесс (обычно эта команда – сочетание клавиш Ctrl-C) .
SIGKILL (номер 9) завершает работу программы. Программа не может ни обработать, ни игнорировать этот сигнал.
SIGCONT (номер 18) возобновляет выполнение процесса, остановленного сигналом SIGSTOP
SIGSTOP (номер 19) приостанавливает выполнение процесса. Как и SIGKILL, этот сигнал не возможно перехватить или игнорировать.
Пример: работает юзер через терминал. Смотрим сеансы pts (ps ax | grep userX) 
[netstat –apnt | grep ssh | grep ‘*’]
Kill –STOP <PID>   	## остановка процесса
Kill –CONT <PID>	## продолжить выполнение остановленного процесса
Kill –KILL <PID>
Установка ОС на VirtualBox VM
Server.corpX. un
Ubuntu-64
2048 ОЗУ
125 GB hdd
----
Сеть: мост
--------

1.Guided – use entire disk
После первого запуска настройка ip адреса.
Пример:
# sudo ifconfig eth0 inet 172.16.1.X/24
# sudo route add default gw 172.16.1.254
Или
# sudo ifconfig enp0s3 inet 172.16.1.X/24
# sudo route add default gw 172.16.1.254
------
Настройка адреса через конфиг:
vi /etc/network/interfaces
auto eth0
iface eth0 inet static
        address 172.16.1.X
        netmask 255.255.255.0
        gateway 172.16.1.254
        dns-nameservers 172.16.1.254
        dns-search corpX.un
Старый способ именования интерфейсов задается в /etc/default/grub
GRUB_CMDLINE_LINUX=""
to
GRUB_CMDLINE_LINUX="net.ifnames=0"
Then, type in:
sudo update-grub
and reboot your system
sudo reboot
-----
Настройка файлов конфигурации.

# sudo vi /etc/hostname и /etc/hosts
Указать имя компьютра, например для машины server:
Server


Sysctl – управление ядра
Systemctl – управление системой инициализации
   





