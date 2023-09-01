# VCS
**Определения:**
- **VCS** - Version Control System - система контроля версий.
- **SCM** - Source Control Managment - система управления исходным кодом.
- **Ревизия** (версия) - одно изменение в VCS.


**VCS** и **SCM** помогают отслеживать изменения (ревизии) в программах, текстовых файлах.<br>


**К VCS относятся:**
- GIT
- Mercurial
- Subversion


**Основные функции VCS:**
1. **хранить историю** в виде отдельных ревизий (изменений);
2. **манипулировать историей:** менять порядок ревизий, удалять, возвращать и т.д.;
3. **анализировать изменения:** кто какие изменения вносит и как часто.

**Ключевая особенность - параллельная работа над одним проектом.**

---


# Командная строка
**Определения:**
- **Командная строка / Терминал / Консоль** - Command-line interface (CLI) -  инструмент взаимодействия с компьютером. По сути является программой с текстовым интерфейсом, которая принимает комманды от пользователя и выполняет их.
- **Git Bush** - консольный инструмент для винды.


**Примечания:**
- ```$``` - значит, что терминал ждет команды.
- создавая файлы, хорошей практикой считается указывание его расширения, так операционной системе проще подобрать программу для запуска.
- ```~``` - домашняя директория.
- все скрытые файлы помечаются точкой вначале (.gitconfig).


**Горячие клавиши для запуска терминала:**
- CTRL + ALT + T (Linux)
- Cmd + space, ввести terminal (MacOS)


## Основные команды 
**Навигация:**
- ```pwd``` - Print Working Directory - вывести текущую рабочую директорию.
- ```cd ~``` - Change Directory -  перейти в домашнюю директорию. ```~``` - домашняя директория.
- ```cd directory-name``` - перейти в указанную директорию.
- ```cd "directory name"``` - перейти в указанную директорию, в имени которой есть пробелы.
- ```cd directory-name1/directory-name2``` - перейти через несколько директорий в указанную.
- ```cd ..``` - перейти на уровень выше (в родительскую директорию).
- ```cd.``` - запустить скрипт или программу, которые в качестве параметра принимают папку.
- ```cd c:/``` или ```cd /c``` - перейти в корневую директорию диска С.
- ```ls``` - List directory contents - вывести содержимое директории.
- ```ls -a``` - вывести содержимое директории со скрытыми файлами.
- ```ls ~``` - вывести содержимое домашней директории, независимо от того, где находишься.
- ```ls ..``` - вывести содержимое родительской директории.


**Создание файлов и директорий:**
- ```touch file-name.txt``` - создать файл с указанным именем.
- ```touch file-name1.txt file-name2.txt``` - создать несколько файлов.
- ```mkdir dir-name``` - Make Directory - создать директорию с указанным именем.
- ```mkdir -p dir-name1/dir-name2``` - создать структуру директорий.


**Работа с файлами и директориями:**
- ```cp file-name.txt target-dir-name``` - копировать файл в указанную директорию.
- ```cp file-name.txt ~``` - копировать файл в домашнюю директорию.
- ```mv file-name.txt target-dir-name``` - переместить файл в указанную директорию.
- ```cat file-name.txt``` - сonCATinate and print - вывести содержимое файла, работает только с текстовыми файлами.
- ```rm file-name.txt``` - удалить файл.
- ```rmdir dir-name``` - удалить директорию.
- ```rm -r dir-name``` - удалить директорию со всем ее содержимым. ```-r``` - recursive.


**Приемы для ускорения работы:**
- **&&** - объединяет несколько команд в одну (```mkdir dir-name && cd dir-name && touch file-name.txt```).
- стрелки **вверх** и **вниз** - вызывают команды из буфера.
- **TAB** - автозаполняет имена директорий и файлов.
---


# Настройка .gitconfig
Чтобы участники проекта знали, кто какие изменения вносил, нужно представиться: указать имя и почту (любые) с помощью команды **git config --global**. Не завимимо от того, где сейчас находишься, эта команда сработает в любом случае. Команды будут выглядеть следующим образом: <br>
```git config --global user.name "Ivan Ivanov"``` <br>
```git config -- global user.email ivanov.yndex.ru```


Все глобальные настройки GIT хранит в файле **.gitconfig** в домашней директории, чтобы это проверить, можно прочесть его с помощью команды: <br>
```cat ~/.gitconfig``` <br>

Альтернативный способ вывести содежимое конфигурайии: <br>
```git config --list```


# Основые GIT
## Создание GIT-репозитория
Чтобы GIT начал отслеживать изменения в проекте, папку с файлами нужно сделать GIT-репозиторием (хранилищем).
Для этого нужно сначала перейти в нее и затем выполнить команду: <br>
```git init``` <br>

Если все сделано правильно, мы увидим: <br>
*"Initialized empty Git repository in..."* <br>

Таким образом мы сделали папку репозиторием, инициализировали ГИТ-репозиторий. <br> 
**Не рекомендуется создавать один репозиторий внутри другого - это может привести к проблемам в отслеживании.**


В подпапке **.git** хранится вся служебная информация. Чтобы *разгитить* директорию, необходимо удалить скрытую папку .git, выполнив команду: <br>
```rm -rf .git``` <br>
```-r``` (рекурия) - удаляет папку с содержимом. <br>
```-f``` (force (заставить)) - узбавляет от подтверждения действия <br>

Подпапка **.git** хранит всю историю изменений, удалив ее восстановить историю будет невозможно.


## Добавление файлов в репозиторий
**Команды:**
- ```git add textfile.txt``` - подготовить файл к сохранению.
- ```git add --all``` - подготовить к сохранению все файлы.
- ```git add .``` - подготовить к сохранению все папку.
- ```git status``` - посмотреть статус репозитория.


Добавив файл в репозиторий, он помечаетя как **"неотслеживаемый"**. Состояние **untracked** значит, что GIT еще не хранит информацию о версиях этого файла и не может отследить, как он изменился. <br>
Зеленый цвет файла означает то, что файл отслеживается, но еще не сохранен. 


**git add** запоминает только состояние файла (контента). Она (команда) не сохраняет содержимое файлов в репозиторий. Само сохранение называют коммитом (совершать, фиксировать). Сделать коммит - сохранить текущую версию файла.


**Аналогия:** git add можно сравнить с добавлением товаров в карзину в интернет-магазине, коммит - с оформлением и оплатой.


Если отредактировать зеленый файл (отслеживаемый), он станет **modified** и будет отображаться сразу в двух списках: зеленом и красном. 
В зеленом он пустой. В красном - с текстом. Поэтому нужно снова выполнить команду ```git add file.txt``` или ```git add --all```.
В таком случае файл будет уже отслеживаться с изменениями.


## Первый коммит
**Команды:**
- ```git commit -m "your message"``` - выполнить коммит. ```-m``` присваивает коммиту сообщение. Оно добавляет понимания, информативности.
- ```git log``` - посмотреть историю коммитов.


**Определения:**
- **Коммит** - одна из основных сущностей в GIT'е. Коммит гарантирует, что все изменения будут сохранены в истории и при желании к ним можно будет откатиться (аналогия: CTRL+Z для всего репозитория). 
- **root-commit** - самый первый коммит в ветке.


**Отличие git add и git commit:** <br>
git add сообщает GIT'у какие файлы нужно сохранить и какую их версию. <br>
git commit - само сохранение.


В сообщениях после коммита можно встретить:
- *mode 100644* - обычный файл
- *mode 100755* - исполняемый файл (.exe)
- *mode 120000* - файлы ссылки (Linux)


**Важно:** <br>
Коммит нужно описывать так, чтобы было понятно, какие изменения были сделаны. <br>
Примеры коммитов:
*"Добавлено важное дело в TODO"* <br>
*"Добавлена сортировка имен"* <br>
*"Исправлена ошибка в цикле"* <br>
*"Добавлены заготовки рекламных текстов"*


Аналогии:
- ```git add``` == добавление товара в карзину.
- ```git commeit``` == фотография.


**Дополнительный пример:** <br>
Мы просим друзей встать рядом, подготовиться и улыбнуться - это команда git add. После мы нажимаем кнопку и делаем снимок - это уже git commit. Сам получившийся снимок будет коммитом.


## Что такое GitHub?
**GitHub** - платформа для хранения проектов и совместной работы с использованием GIT'а. Это сайт, куда можно загружать свои проекты (GIT-репозитории) и делиться ими. **Hub** - узловая станция.


**Отличие Git и GitHub:** <br>
**Git и GitHub** - два разных проекта, развивающихся независимо друг от друга. <br>
**Git** - консольный инструмент для работы с локальным и удаленным репозитоериями. Это проект с открытым исходным кодом. <br>
**GitHub** - платформа для размещения удаленных репозиториев, пренадлежащая Microsoft.


**Другие платформы для командной работы:**
- GitLub
- Bitbucket


**Интересный факт:** <br>
*Ядро Linux разрабатывают с помощью патчей (заплаток, лоскутов с анг.). Это файлы, которые содержат отличия между исходной версией и последующей. Такие патчи рассматривает и объединяет в основную версию ядра лично Линус Торвальд.*


## Создание удаленного репозитория
**Инструкция:**
1. Зайти в свой профиль по ссылке: *https://github.com/username*
2. Перейти на вкладку **Repositories**. Прожать **New**.
3. Задать имя репозиторию.
4. Прожать **Create repository**.


## Что такое SSH?
**Команды:**
- ```ls -la .ssh/``` - проверить наличие SSH-ключа. По-умолчанию они хранятся в домашней дирктории в папка .ssh/

**Важно понимать:** <br>
Чтобы получить доступ к репозиторию на GitHub, нужно предоставить ключ. Он подтверждает личность и права на чтение и изменение данных. 
Без ключа доступ будет ограничен. <br>
Когда компьютеры обмениваются данными в сети, они следуют сетевым протоколам. **Network protocol** - правила обмена данными между компьютерами. 


Один из распространенных протоколов - **SSH** (Secure Shell) - безопасная оболочка. Он обеспечивает безопасность обмена данными в сети. С помощью этого протокола можно получить данные с удаленного компьютера или отправить их на него. Трафик шифруется, поэтому он безопасен. <br>
**SSH использует пару ключей** для обеспечения безопасности:
- **приватный ключ** - хранится только на нашем компьютере и никому не передается. Используется для расшифровки данных.
- **публичный ключ** - доступен всем и используется для шифрования данных. Они могут быть расшифрованы парным приватным ключом.

Эти два ключа связаны и образуют пару. 


Таким образом **SSH-ключ** - это наш <ins>идентификатор</ins> в GitHub, как <ins>ключ от двери</ins>. Он позволяет нам получить доступ к удаленному Git-репозиторию.


Проверка наличия SSH-ключа. По-умолчанию он хранится в домашней дирктории в папка .ssh/ и можно проверить командой: <br>
```ls -la .ssh/```


Если есть файлы с похожим названием: <br>
*id_dsa.pub* <br>
*id_ecdsa.pub* <br>
то ключ уже создан.


## Генерация SSH-ключа
**Команды:**
- ```ssh-keygen -t ed22519 "accountEmail"``` - сгенерировать SSH-ключа (1).
- ```ssh-keygen -t rsa -b 4096 -C "accountEmail"``` - сгенерироват SSH-ключ (2).
- ```ls -a ~/.ssh``` - проверить наличие SSH-ключей.


**Инструкция:**
1. Для генерации пары необходимо использовать программу **ssh-keygen**. Для этого необходимо открыть терминал и выполнить команду: <br>
```ssh-keygen -t ed22519 "accountEmail"``` <br>
Если ошибка, скорее всего система не поддерживает алгоритм шифрования (ed22519). Поэтому выполняем другую команду: <br>
```ssh-keygen -t rsa -b 4096 -C "accountEmail"``` <br>
В том случае, если все сделано правильно, отобразится сообщение: <br>
*"Generating public/private rsa key pair."*
2. После чего нужно указать место хранения ключей. Нажав **enter**, домашний каталог сделается местом для их хранения.  
3. Затем запросится кодовая фраза. Можно не указыавть и просто прожать дважды **enter**.
4. Все, ключи созданы.


Чтобы это проверить, выполним команду: <br>
```ls -a ~/.ssh``` <br>
Должно вывестись два файла, один с расширением **.pub**, другой - без. Тот, что <ins>.pub - публичный</ins>, им можно делиться. Тот, что <ins>без расширния - приватный</ins> и не передается никому.
 

## Связывание SSH-ключа с GitHub-аккаунтом
**Инструкция:**
1. После генерации ключей их нужно скопировать в буфер командой: <br>
```pbcopy < ~/.ssh/id_rsa.pub``` (macOS) <br>
```clip < ~/ssh/id_rsa.pub``` (win) <br>
В качестве альтернативы можно распечатать файл командой: <br>
```cat ~/.ssh/id_rsa.pub``` <br>
и скопировать вручную в буфер через ПКМ.
2. Перейти в GitHub в **Settings** (меню аккаунта). 
3. В меню слева нажать на **SSH and GPG keys**.
4. Выбрать **New SSH key**.
5. Указать заголовок (Title).
6. В поле **Key type** должно быть **Authentication Key**.
7. В поле **Key** скопировать наш ключ из буфера.
8. Прожать **Add SSH key**. <br>
При добавлении нового SSH-ключа GitHub может попросить заново ввести логин и пароль.


Проверить правильность ключа: <br>
```ssh -T git@github.com``` <br>
Если это было первое подключение к серверу, появится сообщение: <br>
*"The authenticity of host 'github.com ..."* <br>
Если не первое, то: <br>
*"Hi UserName! You've successfully authenticated, but GitHub does not provide shell access."*


## Связывание локального репозитория с удаленным
**Инструкция:**
1. Для начала нужно перейти на страницу удаленного репозитория, выбрать тип SSH и скопировать URL.
2. Затем, чтобы привзяать удаленный репозиторий к локальному, нужно перейти в директорию локального репозитоия и выполнить команду: <br>
```git remote add origin ssh-url``` (url вставить с помощью сочитания CTRL + SHIFT + V) <br>
```origin``` (источник) - имя удаленного репозитория, стандартный псевдоним, с помощью которого можно обращаться к удаленному репозиторию.
```ssh-url``` - урл удаленного репозитория.


Чтобы убедиться, что репозитории связаны, необходимо выполнить команду: <br>
```git remote -v``` <br>
```-v``` - краткая форма флага ```--verbose``` (подробный), позволяет показать больше информации в выводе.


Если все сделано правильно, отобразятся две строчки: <br>
*"origin git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch) <br>
origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push)"*


## Отправка изменений на удаленный репозиторий
Каждый коммит сохраняет актуальное состояние файлов. Коммиты хранятся в ветках (branch). <br>
**Коммит** - снимок состояния файлов. <br>
**Ветка** - временная шкала, на которой расположены снимки. Она всегда начинается от одного из коммитов. <br>


В репозитории может существовать сразу несколько веток - параллельных историй изменений. Так же они могут соединяться друг с другом. Самая первая ветка в репозитории появляется автоматически и называется **main**. Ее имя нужно указать при отправки коммитов на удаленный репозиторий или при получении их из него.


Отправить изменения на удаленный репозиторий: <br>
```git push -u origin main```


В первый раз эту команду нужно вызывать с флагом ```-u``` и параметрами: имя удаленного репозитория (origin) и название текущей ветки (main/master). Флаг ```-u``` связывает локальую ветку с одноименной удаленной. В дальнейшем флаг можно опустить.
  
 
## О README
Нужен для того, чтобы другие могли понять, что представляет из себя наш проект. <br>
Как правило в README содержится:
1. Название проекта и его краткое описание:
- кем создан,
- для чего,
- какие решает задачи;
2. Технологии, что встречаются в проекте. Чем наш проект отличается от других.
3. Документация проекта - подробная инструкция, что представляет из себя проект.
4. Планы проекта.


README можно отображать с помощью удобной разметки. **Markdown** - специальный язык разметки. 


## Базовый синтаксис markdown
Заголовки уровнями: <br>
- ```#``` <br>
- ```##``` <br>
- ... и т.д. <br>

Разделительная черта: <br>
- ```---``` <br>

Разрыв строки: <br>
- ```<br>``` <br>
- ```  ``` (два пробела) <br>

Новый параграф: <br>
- два символа переноса (два enter'a) <br>

Выделение курсивом: <br>
- ```*текст*``` <br>
- ```_текст_``` <br>

Сделать полужирным: <br>
- ```**текст**``` <br>

Подчеркивание: <br>
- ```<ins>текст</ins>``` <br>

Зачеркнуть: <br>
- ```~~зачеркнутый текст~~``` <br>

Списки создаются с помощью цифры с точкой: <br>
- ```1.``` <br>
- ```2.``` <br>
- ... и т.д. <br>

Ненумерованный список создается с помощью звездочки/дефиса и пробела
- ```* ``` <br>
- ```- ``` <br>

Оформление ссылок: <br>
- ```[Текст ссылки] (url)``` <br>


## Что такое Хеш?
Хеш коммит можно увидеть при выполнении комманды: <br>
```git log``` <br>
выглядеть он будет как строчка с бессмысленным (на первый взгляд) набором букв и цифр.


**Хеширование** (рубить, крошить, мешанина с анг.) - это способ преобразовать набор данных и получить их "отпечаток" (fingerprint). 


**Информация о коммите** - набор данных: 
- когда был сделан коммит, 
- содержимое файлов в репозитории на момент коммита, 
- ссылка на предыдущий, родительский, коммит.


Git хеширует (преобразует) информацию о коммите с помощью алгоритма **SHA-1** (Secure Hash Algorithm) и получает для каждого коммита свой уникальный хеш - результат хеширования. 


Обычно **хеш** - это короткая строка (40 символов в случае SHA-1), которая состоит из цифр 0-9 и латинских букв A-F (неважно, заглавных или строчных). <br>
Эта строчка обладает следующими свойствами:
- если хеш получить дважды для одного и того же набора входных данных, то результат будет гарантированно одинаковый;
- если хоть что-то в исходных данных поменяется (хотя бы один символ), то хеш снова изменится (причем сильно).


**Хеш** - основной идентификатор коммита.
Гит хранит таблицу соответствий: <br>
хеш --> информация о коммите <br>
Если мы знаем хеш, мы можем узнать все остальное: автора, дату коммита и содержимое закоммиченных файлов. <br> 
При работе с GIT хеши будут встречаться постоянно. Их можно будет передавать в качестве параметра разным GIT-командам, чтобы указать с каким коммитом нужно произвести те или иные операции.


Все хеши и таблицу соответствий GIT сохраняет в служебные файлы. Они находятся в скрытой папке **.git** в репозитории проекта.  


## Анализ логов
**Log** - журнал.


Элементы описания коммита:
- коммит и хеш (строка из цифр и букв),
- автор: имя и эл.почта,
- дата и время создания коммита,
- сообщение коммита.

Получить сокращенный лог: <br>
```git log --oneline``` <br>
В терминале отразятся сокращенные хеши каждого коммита и их комментарии. Сокращенный хеш можно так же использовать как и полный. <br>
**Если выход из просмотра логов не произошел, неоходимо прожать** ```q``` **(quit).**


## Head
Файл **HEAD** (голова) - один из служебных файлов папки **.git**. Он указывает на коммит, который был сделан последним (то есть на самый новый). <br>
Чтобы в этом убедиться, нужно перейти в папку .git и распечатать в нем файл командой: <br>
```cat HEAD``` <br>
Внутри HEAD - ссылка на служебный файл: <br>
*refs/heads/master* <br>
Если заглянуть в этот файл, можно увидеть хеш последнего коммита: <br>
```cat refs/heads/master```


Когда мы делаем коммит, GIT обновляет ссылку **refs/heads/master** - записывает в него хеш последнего коммита. Получаетя что HEAD тоже обновляется. <br>
При работе с  GIT указатель HEAD используется часто, так как многие команды его принимает в качестве параметра. И если нужно передать последний коммит, то вместо написания хеша можно указать просто HEAD - GIT поймет, что мы имеетм ввиду. 
 

## Статусы файлов в GIT
До появления GIT'a выделяли только два статуса:
- уже закоммичен,
- еще не закоммичен.


Одна из ключевых задач GIT - отслеживать изменнеие файлов в репозитории. Для этого каждый файл помечается каким либо статусом. 

**Основные статусы:**
- **untracked** (неотслеживаемый). <br>
Новые файлы в репозитории помечаются как неотслеживаемые. GIT видит, что файл существует, но не следит за изменениями в нем. У неотслеживаемых файлов нет предыдущих версий, зафиксированных в камитах, или через команду git add.

- **staged** (подготовленный)  <br>
После выполнения команды **git add** файл попадает в staging area ("сценную область"), в список файлов, которые войдут в коммит.
В этот момент файл находится в состоянии staged. <br><br>
Раньше мы сравнивали коммит с фотографией. Можно усовершенствовать аналогии. Представлять теперь, что **git add добавляет персонажей (текущее содержимое файлов) на сцену для общей фотографии. А git commit делает снимок всей сцены целиком.** <br><br>
Staging area так же назыавют index (каталог) или cache, а состояние файла staged иногда называют indexed или ceched.

- **tracked** (отслеживаемый) <br>
Оно довольно широкое по смыслу: в него попадают файлы, которые уже были зафиксированны git commit'oм, а так же те, которые были добавлены git add. То есть все файлы, в которых GIT так или иначе отслеживает изменения. 

- **modified** (измененный) <br>
Возникает тогда, когда GIT сравнил содержимое файла с  последней сохраненной версией и нашел отличие. 


## Про Staged и Modified
Команда **git add** добавляет в staging area только текущее содержимое файла. <br>
К примеру, если мы сделаем: <br>
```git add file.txt``` <br> 
и затем изменим file.txt, то новое содержимое файла не будет находиться в staging. GIT сообщит об этом статусом **modified**: файл изменен относительно той версии, которая уже в staging. Чтобы добавить в staging последнюю версию, необходимо снова выполнить команду: <br>
```git add file.txt```


## Жизненный цикл файла в GIT
```mermaid
graph TD;
	A[File life cycle] --> B{Is it a new file?};
	B -- Yes --> C[untracked];
	B -- No --> D[tracked];
	C -- git add --> E[staged, tracked];
	E -- git commit --> F[commited, tracked];
	D -- Changing file --> G[modified, tracked];
	G -- git add --> E[staged, tracked];
```




## Оформление сообщений к коммитам
В выводе команды: <br>
```git log oneline``` <br>
умещается максимум 72 первых символа сообщения, поэтому многие соглашаются на правило: <br>
*"Сообщение не должно быть длинее 72 символов".*


Сообщение коммитов можно сравнить с надписями на коробках в кладовке. Если их нет, то нужную коробку будет сложно найти: придется заглянуть в каждую, чтобы понять, что там. А если надписи есть, то нужная найдется очень быстро.


Общие рекомендации по тому, как правильно писать сообщение коммита. Оно должно быть:
- относительно коротким, легко читаемым;
- информативным;
- быть в одном стиле.


Пример полезного сообщения в репозитории новостного сайта: <br>
*"Исправление опечатки в заголовке главной страницы на хорватском"*


Такое сообщение дает много информации:
- **Исправление опечатки** значит, что была допущена ошибка при наборе. Такое исправление не менет смысл.
- **На хорватском** говорит о том, что переводчикам на другие языки этот коммит можно смело пропускать. 
- **В заголовке** главной страницы указывает, где произошли изменения. 

Пример плохого сообщения для этого же коммита: <br>
*"Исправлена опечатка."* <br>
Это сообщение дает мало инфорамции. 


## Немного о стилях оформления сообщений к коммитам
Все люди разные. Кто-то использует инфинитифы: <br>
*"Исправить сообщение об ошибке Е123"* <br>
Кто-то глаголы в прошедшем времени: <br>
*"Исправил сообщение об ошибке Е123"* <br>
Кто-то существительные: <br>
*"Исправление сообщения об ошибке Е123"*


Пример возможных правил оформления коммитов: 
- длина сообщения от 30 до 72 символов;
- первое слово - глагол в инфинитиве (исправить, дополнить, добавить)
- и т.д.


## Подходы к оформлению сообщений к коммитам
**Подходы:**
- **Корпоративный.** <br>
Обычно в начале сообщения указывают **Jira-ID**, а после текст сообщения: <br>
*git commit -m "LGS-239: Дополнить список пасхалок новыми числами"*
- **Conventional Commits.** <br>
Подходит для репозиториев с исходным кодом. Предполагает формат коммита: <br>
```<type>: <message>``` <br>
**type** - тип изменения (feat, fix). <br>
**feat** (навык) - для новой функциональности. <br>
**fix** - для исправления ошибок. <br>
Пример сообщения: <br>
*git commit -m "feat: Добавить подсчет суммы заказов за неделю"*
- **GitHub стиль.** <br>
GitHub можно использовать для хранения списка задач (ишью) проекта. Если коммит закрывает или решает какую-то задачу, то в его сообщение удобно указывать ссылку на нее. Для этого в любом месте сообщения нужно указать **#<номер задачи>**: <br>
*git commit -m "Исправить #344,  добавить график температуры"* <br>
В таком случае GitHub свяжет коммит и задачу.


**Инфинитив и императив.** Для сообщений на русском языке часто рекомендуют использовать инфинитифы. Для сообщений на английском - повелительное наклонение (imperative): <br>
*"Use library mega_lib_300"* <br>
*"Fix exit button"* <br>
Эти рекомендации сложились исторически. 









 








