# sudo docker run --name nina-mysql -e MYSQL_ROOT_PASSWORD=nina-secret -d mysql:8.0.31

docker run - запуск контейнера

--name nina-mysql имя контейнера

-e MYSQL_ROOT_PASSWORD=nina-secret устанавливаем переменную для окружения
переменная содержит пароль, который мы сами устанавливаем после знака =, логин по умолчанию root

-d запустить докер в фоновом режиме, те в режиме демона

mysql:8.0.31 имя образа, на основании которого будет создан наш контейнер


# sudo docker run --name myphp -d --link nina-mysql:db -p 8081:80 phpmyadmin/phpmyadmin
docker run - запуск контейнера

--name myphp имя контейнера

-d запуск в режиме демона

--link связывает контейнер myphp с nina-mysql

-p 8081:80 пробрасывает порт 8081 с нашего хоста на порт 80 контейнера

phpmyadmin/phpmyadmin имя образа на основе которого будет создан контейнер
![docker run](https://github.com/konopleva-nina/Containerization-courseGB/blob/main/Homework5_scrin1.jpg)
![docker run](https://github.com/konopleva-nina/Containerization-courseGB/blob/main/Homework5_scrin2.jpg)
![resalt](https://github.com/konopleva-nina/Containerization-courseGB/blob/main/Homework5_scrin3.jpg)



вот подробно разобранный docker-compose.yml файл:

# Указываем версию синтаксиса файла docker-compose
version: '3.1'

# Описываем сервисы, которые будут запущены
services:

  # Первый сервис: MySQL сервер
  some-mysql:
    # Используемый Docker образ
    image: mysql:8.0.31
    # Переменные окружения для MySQL
    environment:
      MYSQL_ROOT_PASSWORD: 123-nina


  # Второй сервис: phpMyAdmin
  myphp:
    # Используемый Docker образ
    image: phpmyadmin/phpmyadmin
    # Проброс портов: хост:контейнер
    ports:
      - 8081:80
    # Указываем зависимость от MySQL сервиса
    depends_on:
      - some-mysql
    # Переменные окружения для phpMyAdmin
    environment:
      PMA_HOST: some-mysql

![docker-compose](https://github.com/konopleva-nina/Containerization-courseGB/blob/main/Homework5_scrin5.jpg)
![docker-compose](https://github.com/konopleva-nina/Containerization-courseGB/blob/main/Homework5_scrin6.jpg)
![resalt](https://github.com/konopleva-nina/Containerization-courseGB/blob/main/Homework5_scrin4.jpg)




# Описываем тома
volumes:
  mysql_data:
Пояснение:
version: Указывает версию синтаксиса файла docker-compose. Это нужно для корректного чтения файла Docker Compose.

services: Секция, в которой определяются все контейнеры, которые должны быть запущены.

some-mysql: Имя первого сервиса, запускающего MySQL.

image: Docker образ, который будет использован для этого контейнера.

environment: Переменные окружения для контейнера. В данном случае, устанавливаем пароль root пользователя MySQL.

volumes: Здесь мы монтируем том для сохранения данных MySQL. Это нужно для сохранения данных между перезапусками контейнера.

myphp: Имя второго сервиса, запускающего phpMyAdmin.

depends_on: Указывает, что данный сервис зависит от some-mysql, и нужно сначала его запустить.

PMA_HOST: Указывает на имя хоста MySQL сервера, к которому должен подключиться phpMyAdmin. Здесь это имя сервиса some-mysql.

volumes: В этой секции описываются тома, которые будут использованы. В данном случае, это mysql_data для MySQL.

Этот файл делает то же, что и команды docker run, но в более удобном и управляемом формате.



