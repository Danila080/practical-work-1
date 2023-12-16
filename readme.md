# Шпаргалка по инициализации и синхронизации локального и удаленного хранилищ
---

**Создание директории**
```
mkdir <directory-name>
cd /<directory-name>
git init
```
---

**SSH-ключ**

**Проверка наличия SSH-ключа**
```
cd ~  #переход в домашнюю директрию
ls -la .ssh/ #вывод списка имеющихся SSH-ключей
```

**Генерация SSH-ключа**
```
ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" 
```
Если вы видите сообщение об ошибке, то, скорее всего, ваша система не поддерживает алгоритм шифрования ed25519 ->
```
ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" 
```
 После ввода отобразится следующее сообщение
```
Generating public/private rsa key pair. #сгенерированы публичный и приватный ключи 
Enter a file in which to save the key (C:\Users\<имя_пользователя>\.ssh\):[Press enter] 
```
Для проверки того, что ключи сгенерировались, требуется ввести следующую команду:
```
ls -a ~/.ssh 
```

**Привязывание SSH-ключа**

Скопировать содержимое ключа в буфер обмена:
```
clip < ~/.ssh/id_rsa.pub 
clip < ~/.ssh/id_ed25519.pub #для ed25519
 ```

**Создание файлов в созданной директории и их выгрузка в удаленное хранилище**
```
cd /<directory-name>
touch <file-name.extantion>
git add <file-name.extansion>
git commit -m 'comment for commit'
git push -u origin main #при первой синхронгизации хранилищ (если выдается ошибка, то следует заменить main на master)
git push #при последующих синхронизациях
```
---

**Создание readme.md**
```
cd /<directory-name>
touch readme.md
```
Данный файл следует писать согласно рекомендациям по Markdown, представленным по следующим ссылкам:
[Шпаргалка по Markdown](https://gist.github.com/fomvasss/8dd8cd7f88c67a4e3727f9d39224a84c#alt-h1)

[Гайд по Markdown](https://www.markdownguide.org/cheat-sheet/)
