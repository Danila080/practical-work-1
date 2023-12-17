# Шпаргалка по инициализации и синхронизации локального и удаленного хранилищ
---

## Создание директории ##
```
mkdir <directory-name>
cd /<directory-name>
git init
```
---

## SSH-ключ

### Проверка наличия SSH-ключа
*Переход в домашнюю директорию:*
```
cd ~ 
```
*Вывод списка имеющихся SSH-ключей:*
```
ls -la .ssh/ 
```

### Генерация SSH-ключа
```
ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" 
```
*Если вы видите сообщение об ошибке, то, скорее всего, ваша система не поддерживает алгоритм шифрования ed25519 ->*
```
ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" 
```
*После ввода отобразится следующее сообщение*
*Сгенерированы публичный и приватный ключи:* 
```
Generating public/private rsa key pair. 
Enter a file in which to save the key (C:\Users\<имя_пользователя>\.ssh\):[Press enter] 
```
*Для проверки того, что ключи сгенерировались, требуется ввести следующую команду:*
```
ls -a ~/.ssh 
```

### Привязывание SSH-ключа

*Скопировать содержимое ключа в буфер обмена:*
```
clip < ~/.ssh/id_rsa.pub 
```
*Для ed25519:*
```
clip < ~/.ssh/id_ed25519.pub 
 ```

### Создание файлов в созданной директории и их выгрузка в удаленное хранилище
```
cd /<directory-name>
touch <file-name.extantion>
git add <file-name.extansion>
git commit -m 'comment for commit'
```
*При первой синхронизации хранилищ (если выдается ошибка, то следует заменить main на master):*
```
git push -u origin main 
```
*При последующих синхронизациях:*
```
git push 
```
---

## Создание readme.md
```
cd /<directory-name>
touch readme.md
```
Данный файл следует писать согласно рекомендациям по Markdown, представленным по следующим ссылкам:
[Шпаргалка по Markdown](https://gist.github.com/fomvasss/8dd8cd7f88c67a4e3727f9d39224a84c#alt-h1)

[Гайд по Markdown](https://www.markdownguide.org/cheat-sheet/)

---
## Log
*Вывод информации о коммитах:*
```
git log
```
*Вывод сокращенного лога:*
```
git --oneline
```
*В папке .git содержится файл HEAD, в котором ссылка на служебный файл:*
```
refs/heads/master
```
*или*
```
refs/heads/main
```
В вышеуказанном файле содержится хеш последнего коммита. Вместо хеша последнего коммита можно написать слово **HEAD**.

---
## Статусы 
- **untracked** - новые файлы в Git-репозитории, Git видит, что данный файл существует, но не отслуживает изменения в нем.
- **staged** - после выполнения команды *git add* файл находится в этом состоянии.
- **tracked** - все файлы, в которых Git отслеживает изменения.
- **modified** - означает, что Git сравнил содержимое файла с последней сохранённой версией и нашёл отличия. Например, файл был закоммичен и после этого изменён.

![Жизненный цикл файла в Git](https://pictures.s3.yandex.net/resources/M2_T5_1686651284.png 'Жизненный цикл файла в Git')
### Git status
- команда ```git status``` показывает, что происходит с файлом;
- ```git status``` явно показывает состояния файлов: ```untracked```, ```staged```, ```modified```;
- ```git status``` подсказывает, какие команды можно выполнить, чтобы поменять состояние файла.
### Оформление сообщений к коммитам
У каждого коммита в Git есть сообщение — то, что передаётся после параметра ```-m```. Например: ```git commit -m 'Добавление раздела про оформление коммитов'```.\
Общие правила по составлению описания к коммитам. Они должны быть:
- относительно короткими, чтобы легко читались;
- информативными.\
**Основные подходы к оформлению коммитов:**
- корпоративный;
- Conventional Commits;
- GitHub-стиль.