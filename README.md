# Setup

Всё это легко гуглится, так что если что-то не получается, можно поискать в интернете решения.

Ресурсы:

[Консольные команды linux и macos (пока вам будет достаточно первых 5 пунктов)](https://omgubuntu.ru/basic-linux-commands-for-beginners/)

[Документация git](https://git-scm.com/book/ru/v2)

[Упражнения для знакомства с git](https://gitexercises.fracz.com/)

[Найти фунцию в Haskell по ее типу](https://hoogle.haskell.org/)

[Преобразование функций в бесточечный вид](http://pointfree.io/)

## Как установить git

Открываем консоль/треминал.

Если у вас `linux`, прописываем команду

```
$ sudo apt install git
```

NB: значок доллара - это не часть команды, он помогает понимать, что перед вами цитата из консоли.

Если же у вас `macos`, сначала необходимо установить утилиту `homebrew` (если у вас ее еще нет) следующей командой в терминале:

```
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

А затем прописать команду

```
$ brew install git
```

И напоследок

```
$ export PATH=/usr/local/bin:$PATH
```

## Как настроить git

Первое, что вам следует сделать после установки git - указать ваше имя и адрес электронной почты. Это важно, потому что каждый коммит в git содержит эту информацию, и она включена в коммиты, передаваемые вами, и не может быть далее изменена:

```
$ git config --global user.name "Sergey Obritaev"
$ git config --global user.email serjobrit@gmail.com
```

NB: Если что, вместо этих имени и почты, надо подставить ваши.

Если вы не понимаете, как пользоваться какой-то командой, вы можете вызвать страницу руководства.
К примеру, вы забыли, как использовать `config`. Напишите в консоль

```
$ git config -h
```

В самом начале вам покажут общий шаблон работы команды, а потом варианты ее использования.
Если на английском ничего не понятно, вам поможет google.


## Как установить stack

`linux`:

```
curl -sSL https://get.haskellstack.org/ | sh
```

`macos`:

```
$ brew install haskell-stack
```

Установка может длиться очень долго, не волнуйтесь по этому поводу.

## Как настроить stack

Напишите в консоль следующие команды, чтобы скачать необходимые библиотеки:

```
$ stack update
$ stack install HUnit
$ stack install hspec
$ stack install tasty
$ stack install tasty-hspec
$ stack install tasty-hunit
```

## Как получить себе репозиторий

Регистрируемся на `github`.

На странице этого репозитория справа сверху нажимаем кнопку `Fork`, чтобы создать свою копию этого репозитория.
Надо немного подождать, пока репозиторий будет создаваться. После чего надо скопировать его ссылку.

Заходим в консоль. При помощи команды `cd` перемещаемся в папку, в которой вы хотите, чтобы находился ваш репозиторий.
Далее пишем в консоль команду `git clone your_link`, где `your_link` - это ссылка на ваш репозиторий, которую вы уже скопировали.
К примеру:

```
$ git clone https://github.com/Peltorator/tinkoff_haskell_2020
```

Скорее всего вам надо просто поменять слово `Peltorator` на ваш ник на гитхабе.

Ура, у вас создался репозиторий на компьютере. Моете в него заходить. Это как обыная папка с файлами.


# Выполнение заданий

В папке `src` находится файл `Tasks.hs`.
В нем есть несколько функций. Вам необходимо заменить `undefined` на корректное тело фунции.

Тесты находятся в папке `test/Test/`. Вы можете дописывать свои тесты по аналогии с уже существующими.

## Как запускать код и проверять его на тестах

Запускаем консоль, переходим в папку с проектом.

Запустить интерпретатор `ghci`:

```
$ ghci
```

Запустить интерпретатор `ghci`, загрузив в него год из вашего файла:

```
$ ghci main.hs
```

Собрать проект:

```
$ stack build
```

Запустить проект на тестах:

```
$ stack test
```


## Как сдавать задания

После того, как вы выполнили все задания, их необходимо отправить на проверку.

Вам помогут следующие команды:

```
$ git status
```

Даст вам информацию о том, какие файлы добавлены в будущий коммит, а какие еще нет.

```
$ git add a.cpp
```

Добавит файл `a.cpp` в будущий коммит.

```
$ git commit -m"your message goes here"
```

Сделать коммит.

```
$ git log
```

Покажет вам историю коммитов.

```
$ git push origin master
```

Необходимо выполнить после коммитов, когда вы хотите выложить ваши результаты на гитхаб.

Когда все ваши изменения уже выгружены, зайдите в ваш репозиторий на гитхабе.
Стоит проверить, что над списком файлов указан ваш последний коммит (можно проверить по сообщению, времени выгрузки и хэшу).

После чего необходимо создать `pull request`.
Над списком файлов есть несколько кнопочек. Одна из которых называется `new pull request`.
Нажимаем на нее, Проверяем, что стрелочка ведет из вашего репозитория в мой и ветки выбраны `master`.
Затем необходимо заполнить название пул-реквеста. Оно должно содержать ваше имя. Пример:

```
Egor Gorbachev
```

Снизу можно по желанию оставить комментарий, если вам нужно передать какую-то информацию мне.
И в конце жмем кнопочку `Create pull request`.

Вас перенесет в созданный `pull request`. Там мы будем вести переписку по поводу вашего задания.

Необходимо, чтобы функции работали правильно на любом входе
и при этом были написаны в красивом функциональном стиле с приятным кодстайлом.
