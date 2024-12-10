
# Лабораторная работа 5.
## Задание №1
Будем работать в Git Bash
1) Создадим репозиторий `inf5` и клонируем его с помощью команды
   ```
   git clone <ссылка на репозиторий>
   ```
   ![image](https://github.com/user-attachments/assets/884a83f0-1571-41b0-8c7e-170c292321f3)

2) Перейдем в папку репозитория:
   ```
   cd inf5
   ```
   
3) Проверим наличие папки .git/hooks/ командой:
   ```
   ls -la .git/hooks/
   ```
   ![image](https://github.com/user-attachments/assets/64a84824-7f02-406a-a2c6-5a46580960aa)

4) Перейдем в эту папку и создадим файл pre-commit
   ```
   cd .git/hooks/ && nano pre-commit
   ```
   ![image](https://github.com/user-attachments/assets/4ac3264d-f996-40c1-9eba-ef539003141e)

5) Напишем в нем скрипт для проверки файла перед тем, как сделать commit
   ![image](https://github.com/user-attachments/assets/9cebf4b4-7812-4f16-b34a-9af9795c75dc)

   После сохранения содержимое станет таким:
   
   ![image](https://github.com/user-attachments/assets/afcafcb2-4aec-4ad2-a16e-bd922afdd5a4)

6)  Сделаем файл исполняемым
     ```
     chmod +x pre-commit
     ```
    ![image](https://github.com/user-attachments/assets/2f55c38d-4040-445d-9ee4-875ead0cdb3f)

7) Вернемся в папку репозитория и создадим новый текстовый файл `task_1_1.txt`
   ```
   nano task_1_1.txt
   ```
   Внесем в него какой-то текст. Главное, чтобы в нем присутствовало слово `Автор`:
   ![image](https://github.com/user-attachments/assets/430c6c71-1728-46cb-a0d7-b0b4b1bc60eb)

8) Сохраним файл, попробуем сделать commit и отправить его в репозиторий
   ```
   git add task_1_1.txt
   git commit -m "Добавлен корректный текстовый файл"
   git push origin main
   ```
   ![image](https://github.com/user-attachments/assets/9ed173cc-bb34-4d53-a088-d6fc168bb285)
   
   После выполнения команды `git commit -m "Добавлен корректный текстовый файл"` видим сообщение о том, что файл прошел проверку, и в нем есть слово "Автор"

9) Зайдем в наш репозиторий и увидим, что файл `task_1_1.txt` успешно добавлен вместе со своим содержимым
   
    ![image](https://github.com/user-attachments/assets/4dfe5341-efff-4a01-be81-6fc4505a6453)
   
    ![image](https://github.com/user-attachments/assets/32a2ac26-acc5-4107-b284-4764511531d6)

10) Аналогично создадим файл `task_1_2.txt`, в котором не будет слова `Автор` и повторим те же действия, что с предыдущим файлом
    ```
    nano task_1_2.txt
    git add task_1_2.txt
    git commit -m "Попробуем добавить некорректный файл"
    ```
    
    ![image](https://github.com/user-attachments/assets/e18c69d3-c51c-4437-89b8-4bb5a20ef536)
    
    ![image](https://github.com/user-attachments/assets/74c741df-6e3e-4563-bec3-9ba942c40728)

    Получаем сообщение о том, что слова "Автор" нет в файле -> мы не можем сделать commit и  отправить изменения на сайт:
    
    ![image](https://github.com/user-attachments/assets/4796bbad-27a7-4992-a3e2-33993785665c)

    Действительно, выполня все эти действия и перейдя на сайт репозитория, мы не увидим там файл `task_1_2.txt`

11) Чтобы убрать файл из раздела тех, которые будут закоммичены, отменим предыдущее действие, а также проверим состояние рабочего каталога и статус файлов
    ```
    git reset HEAD task_1_2.txt
    git status
    ```
    ![image](https://github.com/user-attachments/assets/445ada37-35c1-4fd9-95d2-06c836ab6356)

## Задание №2
1) Проверим, что Git Flow установлен
   ```
   git flow version
   ```
   ![image](https://github.com/user-attachments/assets/d0a6da21-9385-4e4e-a282-d9568d37ff8e)

2) Инициализируем Git Flow и оставим название веток по умолчанию
   ```
   git flow init
   ```
   ![image](https://github.com/user-attachments/assets/ae666ae9-6135-4e50-a830-a8e81e550de3)

3)  Создадим ветку для нового функционала
     ```
     git flow feature start task-management
     ```
    ![image](https://github.com/user-attachments/assets/9b4bc328-ad72-4e69-90b4-fdd439ecb68f)

4) Создадим новый Python-файл `task_manager.py` и откроем его
   ```
   nano task_manager.py
   ```
   Напишем в файле такой скрипт:

   ![image](https://github.com/user-attachments/assets/caf30c8e-ce4e-4453-af73-1638152537f4)

5) Закоммитим это файл с помощью команд
   ```
   git add task_manager.py
   git commit --no-verify -m "Добавлен функционал управления задачами"
   ```
   --no-verify необходимо для того, чтобы отключить проверку файлов из предыдущего задания
   ![image](https://github.com/user-attachments/assets/eb59661c-b36c-4e5c-8bf4-c2e693b68851)
   ![image](https://github.com/user-attachments/assets/dcf2957a-359e-4d4c-b877-77a14be92366)
   
6) Предположим, что мы закончили разработку, поэтому удалим ветку и переключимся на ветку develop с помощью команды:
    ```
    git flow feature finish task-management
    ```
    ![image](https://github.com/user-attachments/assets/822d965f-a0ad-4f0b-855e-d7f1fd414a5a)

7) Создадим релиз при помощи команд:
    ```
    git flow release start v1.0.0
    echo "v1.0.0" > version.txt
    git add version.txt
    git commit -m "Обновлена версия для релиза v1.0.0"
    git flow release finish v1.0.0
    ```

   ![image](https://github.com/user-attachments/assets/0038b6d1-4e2d-465d-bade-a1750f6c2993)

   ![image](https://github.com/user-attachments/assets/2fddb6ca-908d-4f27-a3e6-f43cdbeb353b)


8) Создадим ветку для срочного исправления ошибки:
    
    ```
    git flow hotfix start hotfix-1.0.1
    ```
    
    ![image](https://github.com/user-attachments/assets/1406105b-50d9-4f54-a1e4-9b150968f335)


9) "Исправим ошибку" в файле task_manager.py
    
    ![image](https://github.com/user-attachments/assets/cc199bfb-a049-4fdc-baf6-b7eaa1128f3f)


10) Внесем изменения в локальный репозиторий в ветку master:
    
    ```
    git add file_with_error.py
    git commit -m "Исправлена критическая ошибка"
    git flow hotfix finish hotfix-1.0.1
    ```
    
    ![image](https://github.com/user-attachments/assets/b0a80c15-f823-48e2-a6ec-e0ab19df9de9)
    
    ![image](https://github.com/user-attachments/assets/c2639da3-1c5c-4457-8ef7-c9c4c7424e65)


11) Отправим изменения в ветку develop
    ```
    git checkout develop
    git push origin develop
    ```
    ![image](https://github.com/user-attachments/assets/03a7c0ef-449c-4d3a-b0a0-eac1b633bfe2)


12) Отправим изменения в ветку main
    ```
    git checkout main
    git push origin main
    ```
    ![image](https://github.com/user-attachments/assets/45aa504b-a545-4dce-9294-1204b9d1a7f4)
    
    ![image](https://github.com/user-attachments/assets/70662fba-3a45-4be0-931b-81f73a81aece)
    
13) Перейдем в наш репозиторий и увидим:

    ![image](https://github.com/user-attachments/assets/01cbf51f-a611-4047-8bf2-91ead1efc313)


