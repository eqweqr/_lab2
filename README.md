# _lab2
***LAB2***
**Выполнил: Вечеринин Артем ИУ8-22**

***Homework***
***PART 1***

1. **Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).**
```bash
$ git clone git@github.com:eqweqr/_lab2.git
$ touch README.md

2. **Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.**
$ git add .
$ git commit -m 'add Readme.md'
$ git push origin master 
```
<details>
<summary>Терминал</summary>
Перечисление объектов: 3, готово.
Подсчет объектов: 100% (3/3), готово.
При сжатии изменений используется до 8 потоков
Сжатие объектов: 100% (2/2), готово.
Запись объектов: 100% (3/3), 314 байтов | 314.00 КиБ/с, готово.
Всего 3 (изменения 0), повторно использовано 0 (изменения 0)
To github.com:eqweqr/_lab2.git
 * [new branch]      master -> master
</details>

3. **Создайте файл hello_world.cpp в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу Hello world на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку using namespace std;.**
```bash
$ touch hello_world.cpp
$ cat >hello_world.cpp<<EOF
#include <iostream>
using namespace std;
int main(){
cout<<"Hello world";
return 0;
}
EOF
```
4. **Добавьте этот файл в локальную копию репозитория.**
```bash
$ git add hello_world.cpp
```
5. **Закоммитьте изменения с осмысленным сообщением.**
``` bash
$ git commit -m 'add hello_world.cpp'
```
6. **Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение Hello world from @name, где @name имя пользователя.**
```bash
cat> hello_world.cpp <<EOF
#include <iostream>
using namespace std;
int main(){
string name;
cin>>name;
cout<<"Hello world from "<<name;
return 0;
}
EOF
```
7. **Закоммитьте новую версию программы. Почему не надо добавлять файл повторно git add?**
```bash 
$ git commit hello_world.cpp -m 'changing hello_world.cpp
```
<details><summary>Ответ</summary>
Не нужно использовать git add тк мы не добавляет новый файл,а лишь редактируем старый
</details>

8.**Запуште изменения в удалёный репозиторий.**

```bash
$ git push origin master 
```
<details><summary>Консоль</summary>
Перечисление объектов: 7, готово.
Подсчет объектов: 100% (7/7), готово.
При сжатии изменений используется до 8 потоков
Сжатие объектов: 100% (6/6), готово.
Запись объектов: 100% (6/6), 728 байтов | 728.00 КиБ/с, готово.
Всего 6 (изменения 0), повторно использовано 0 (изменения 0)
To github.com:eqweqr/_lab2.git
   d02fe3d..fd1ba40  master -> master
</details>

9. **Проверьте, что история коммитов доступна в удалёный репозитории.**

----

***Part 2***
1. **В локальной копии репозитория создайте локальную ветку patch1**
```bash
$ git checkout -b patch1
```

2. **Внесите изменения в ветке patch1 по исправлению кода и избавления от using namespace std;.**
```bash 
$ cat >hello_world.cpp <<EOF
#include <iostream>
int main(){
std::string name;
std::cin>>name;
std::cout<<"Hello world from"<<name;
return 0;
}
EOF
```
3. **commit, push локальную ветку в удалённый репозиторий.**
```bash
$ git commit hello_world.cpp -m 'clear style'
$ git push origin patch1
```
4. **Проверьте, что ветка patch1 доступна в удалёный репозитории.**
5. **Создайте pull-request patch1 -> master.**
6. **В локальной копии в ветке patch1 добавьте в исходный код комментарии.**
```bash
cat >hello_world.cpp <<EOF
#include <iostream>
int main(){
std::string name;// Создание переменной name
std::cin>>name;//инициализация переменной
std::cout<<"Hello world from "<<name;//Вывод сообщения в консоль
return 0;
}
EOF
```
7. **commit, push.**
```bash
$ git commit hello_world.cpp -m 'Добавление комментариев в файл'
$ git push origin patch1
```
8. **Проверьте, что новые изменения есть в созданном на шаге 5 pull-request**
9. **В удалённый репозитории выполните слияние PR patch1 -> master и удалите ветку patch1 в удаленном репозитории.**
10. **Локально выполните pull.**
```bash 
$ git pull origin master
```
<details>
<summary>Консоль</summary>
git pull origin master
remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
Распаковка объектов: 100% (1/1), 614 байтов | 614.00 КиБ/с, готово.
Из github.com:eqweqr/_lab2
 * branch            master     -> FETCH_HEAD
   1e9e2b0..a57e53a  master     -> origin/master
Обновление c2a2eaf..a57e53a
Fast-forward
</details>

11. **С помощью команды git log просмотрите историю в локальной версии ветки master.**
```bash 
$ git log master
```
<details>
<summary>Консоль</summary>
Author: eqweqr <49245539+eqweqr@users.noreply.github.com>
Date:   Thu Mar 10 16:20:47 2022 +0300

    Merge pull request #1 from eqweqr/patch1
    
    clear style

commit 84ae462403b8f10020b8a718603ec2bb83a522fd (origin/patch1)
Author: astarot <artem.vecherinin@mail.ru>
Date:   Thu Mar 10 16:18:44 2022 +0300

    Добавление комментариев в файл

commit e3fe449c5fdd40dfe328f96ec205d644e3058029
Author: astarot <artem.vecherinin@mail.ru>
Date:   Thu Mar 10 16:10:03 2022 +0300

    clear style

commit fd1ba4005a71d0c785a26af74bba8e71a5ec8165
Author: astarot <artem.vecherinin@mail.ru>
Date:   Thu Mar 10 15:57:57 2022 +0300

    changing hello_world.cpp

commit 5c5d75ec3da16684bfed51ad01c4d31342edd9ce
Author: astarot <artem.vecherinin@mail.ru>
Date:   Thu Mar 10 15:53:26 2022 +0300

    add hello_world.cpp

commit d02fe3d55a92403588f3b4b1692e9c4f05a067e1
Author: astarot <artem.vecherinin@mail.ru>
Date:   Thu Mar 10 15:49:00 2022 +0300

    add Readme.md
</details>

12. **Удалите локальную ветку patch1.**
```bash 
$ git branch -d patch1
```
***Part 3***
1. **Создайте новую локальную ветку patch2.**
```bash
$ git checkout -b patch2
```
2. **Измените code style с помощью утилиты clang-format. Например, используя опцию -style=Mozilla**
```bash 
$ clang-format -style=Mozilla -i hello_world.cpp
```
3. **commit, push, создайте pull-request patch2 -> master.**
```bash
$ git commit -am 'patch2 new style'
$ git push origin patch2
```
<details><summary>Консоль</summary>
Перечисление объектов: 7, готово.
Подсчет объектов: 100% (7/7), готово.
При сжатии изменений используется до 8 потоков
Сжатие объектов: 100% (4/4), готово.
Запись объектов: 100% (4/4), 3.04 КиБ | 3.04 МиБ/с, готово.
Всего 4 (изменения 0), повторно использовано 0 (изменения 0)
remote: 
remote: Create a pull request for 'patch2' on GitHub by visiting:
remote:      https://github.com/eqweqr/_lab2/pull/new/patch2
remote: 
To github.com:eqweqr/_lab2.git
 * [new branch]      patch2 -> patch2
 </details>

 4. **В ветке master в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.**

 5. **Убедитесь, что в pull-request появились конфликтны.**
 6. **Для этого локально выполните pull + rebase (точную последовательность команд, следует узнать самостоятельно). Исправьте конфликты.**
 ```bash 
$ git checkout master
$ git pull origin master
$ git checkout patch2
$ git add hello_world.cpp
$ git rebase master
$ git rebase --skip
 ```
 7. **Сделайте force push в ветку patch 2**
 ```bash 
$ git push -f origin patch2
 ```
 <details>
 <summary>Консоль</summary>
 Всего 0 (изменения 0), повторно использовано 0 (изменения 0)
To github.com:eqweqr/_lab2.git
 + b47d59a...1ccbf2c patch2 -> patch2 (forced update)
 </details>

 8. **Убедитесь, что в pull-request пропали конфликты.**
 9. **Вмержите pull-request patch2 -> master.**
