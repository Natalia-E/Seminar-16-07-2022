# Инструкция по работе с git и удалёнными репозиториями

## Что такое git?
*Git* одна из реализаций распредённых систем контроля версий. *Git* на данный момент является самой полулярной реализацией. Самой популярной реализацией *Git* является [GitHub](https://github.com) 

## Подготовка репозитория
Для того, чтобы создать репозиторий используется команда *git init*. Для этого необходимо написать в терминале в папке будущего репозитория *git init* 

## Состояние репозитория
Для того, чтобы посмотреть состояние репозитория, используется команда *git status* Для этого в терминале с папкой-репозиторием необходмо написать *git status*, и возможно увидеть несколько состояний:
1. Nothing to commit - репозиторий не содержит изменений
2. Unversioned file - папка содержит файл, к которому не добавлена версионность

# Просмотр сделанных изменений
Для того, чторбы просмотреть разницу между текущей версией файла, и версией файла в полследнем коммите, используется команда *git diff*. Для этого в терминале с папкой с репозиторием, напишите *git diff*

## Создание коммитов

### Добавление файла к коммиту

Для добавления файла к коммиту используется команда *git add*. Пишется она следующим образом *git add <имя файла>* в терминале в папке с созданным репозиторием.

### Создание нового коммита

Для создание нового "сохранения" испольузется команда *git commit*. Используется она следующим образом: в терминале с папкой-репозиторием пишется *git commit -m <сообщение к коммиту>*. Сообщение к коммиту писать **ОБЯЗАТЕЛЬНО**!!! 

## Журнал изменений
Для просмотра журнала измений используется команда *git log*. Для этого в терминале в папке с репозиторием достаточно написать *git log*

## Перемещение между "сохранениями"
Для перемещения между сохранениями используется команда *git checkout*. Для того, чтобы перемиститься на указанный коммит в терминале в папке с репозиторием пишем *git checkout <номер коммита>*. **Номер коммита** берется из журнала изменений, о котором сказано выше. После перемещния на указанный коммит мы попадаем в состояние **detached head*. Чтобы вернуться к обычной работе, необходимо написать *git checkout master*.

## Ветки в git
Ветки в *git* нужны, чтобы работать с "чистовиком" и "черновиками". Для того, чтобы создать новую ветку используется команда *git branch*. В терминале в папке с репозиторием, напишите *git branch <название ветки>*.

## Создание веток 
Ветки в GIT – представляют собой указатель на снимок изменений, - коммит. 
Если нужно добавить новую возможность или исправить ошибку (незначительную или серьезную), создается  новая ветка, в которой будут размещаться эти изменения.
Для того, чтобы создать ветку необходимо воспользоваться командой *“git branch”*  имя ветки.

## Слияние веток 
Процедура объединения веток называется слияние (merge). Для слияния текущей ветки с какой-либо другой используется команда “git merge” имя_ветки. В результате выполнения этой команды в текущей ветке появится новый коммит. Этот коммит будет иметь два предка – последние коммиты обоих веток, участвующих в слиянии. Содержимое этого коммита будет включать содержимое коммитов обоих веток.

## Управление ветками
Отображение списка веток в репозитории осуществляется командой *“git branch –list”* или *“git branch”*. Удаление указанной ветки осуществляется командой *“git branch -d <ветка>”*. Это «безопасная» операция, поскольку Git не позволит удалить ветку, если в ней есть неслитые изменения. Принудительное удаление указанной ветки, даже если в ней есть неслитые изменения осуществляется 
командой *“git branch -D <ветка>”*. Изменение имени текущей ветки проводится командой *“git branch -m <ветка>”*. Вывод списка всех удаленных веток – команда  *“git branch -a”*.

## Конфликты GIT
Конфликт во время слияния может произойти в двух отдельных точках — при запуске и во время процесса слияния. Строка ======= является «центром» конфликта. Все содержимое между этим центром и строкой <<<<<<< HEAD находится в текущей ветке main, на которую ссылается указатель HEAD. А все содержимое между центром и строкой >>>>>>> new_branch_to_merge_later является содержимым ветки для слияния.

## Команды для решения конфликтов
Команда *“git status”* часто используется во время работы с Git и помогает идентифицировать конфликтующие во время слияния файлы.
При передаче аргумента –merge для команды *“git log”* будет создан журнал со списком конфликтов коммитов между ветками, для которых выполняется слияние.
Команда *“git diff”* помогает найти различия между состояниями репозитория/файлов. Она полезна для выявления и предупреждения конфликтов слияния.

### Инструменты на этапе начала слияния 
Команда *“git checkout”* может использоваться для отмены изменений в файлах или для изменения веток.
Команда *“git reset –mixed”* может использоваться для отмены изменений в рабочем каталоге или в разделе проиндексированных файлов.

### Инструменты на этапе слияния 
При выполнении команды *“git merge –abort”* процесс слияния будет прерван, а ветка вернется к состоянию, в котором она находилась до начала слияния.
Команду *“git reset”* можно использовать для разрешения конфликтов, возникающих во время выполнения слияния, чтобы восстановить заведомо удовлетворительное состояние конфликтующих файлов.

## Работа с удаленными репозиториями

## Добавление репозитория
Для добавления удаленного репозитория к локальному репозиторию есть команда *git remote add*.Ссылку на отдаленный репозиторий можно взять, нажав на большую зеленую кнопку Code на странице репозитория на GitHub.

## Отключение удаленного репозитория от локального
Для того, чтобы забыть удаленный репозиторий существует команда git remote remove. В качестве имени репозитория нужно передавать то имя, которое вы указывали в команде git remote add. Заметьте, данная команда не удаляет удаленный репозиторий с сервера, она удаляет только подключение вашего репозитория к удаленному. 

## Изменение имени удаленного репозитория
Для того, чтобы переименовать репозиторий  существует команда git remote rename. 

## Скачивание удаленного репозитория
Для того, чтобы скачать удаленный репозиторий необходимо использовать команду *git clone*. В терминале, котором открыта любая пустая папка, необходимо написать *git clone <ссылка на репозиторий>*.Репозиторий скачается в папку, имя которой будет совпадать с именем репозитория.

## Получение изменений из удаленного репозитория
Для того, чтобы получить изменения из удаленного репозитория, в Git предусмотрена команда git fetch. Команда git fetch используется для синхронизации локальных ссылочных объектов с этими же объектами в удаленном репозитории. Рабочую копию она не меняет.
Чтобы синхронизировать локальную рабочую копию с удаленным репозиторием, нужно слить удаленные ветки в локальные. Сделать это можно уже знакомой командой git merge.

## Скачивание изменений с удаленного репозитория
Для того, чтобы скачать изменения с удаленного репозитория необходимо использовать команду *git pull*.В терминале в папке с репозиторием, связанной  удаленным с репозиторием, пишем *git pull origin <название ветки>*, для того чтобы принять изменения из указанной ветки отдаленного репозитория в текущую ветку.

## Отправка изменений в GitHub
Для отправки изменений в удаленный репозиторий необходимо использовать команду *git push*. Для этого в терминале с папкой, связанной с удаленным репозиторием, пишем команду *git push origin <название ветки>*, где <название ветки> - это ветка в удаленном репозитории, куда необходимо отправить совершенные изменения.
