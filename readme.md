# Шпаргалка по инициализации и синхронизации локального и удаленного хранилищ


**Создание директории**
```
mkdir <directory-name>
cd /<directory-name>
git init
```

**Создание файлов в созданной директории и их выгрузка в удаленное хранилище**
```
cd /<directory-name>
touch <file-name.extantion>
git add <file-name.extansion>
git commit -m 'comment for commit'
git push -u origin main # при первой синхронгизации хранилищ (если выдается ошибка, то следует заменить main на master)
git push # при последующих синхронизациях
```

**Создание readme.md**
```
cd /<directory-name>
touch readme.md
```

Данный файл следует писать согласно рекомендациям по Markdown, указанным в шпаркгалке, приложенной ниже
[Шпаргалка по Markdown]https://gist.github.com/fomvasss/8dd8cd7f88c67a4e3727f9d39224a84c#alt-h1

