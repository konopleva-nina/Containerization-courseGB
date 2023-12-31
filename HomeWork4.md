## Создание Dockerfile 

FROM ubuntu:20.04
Используйте инструкцию RUN, чтобы выполнить команды внутри контейнера во время сборки образа. Например, для обновления пакетов в Ubuntu и установки Python 3, вы можете написать:


RUN apt-get update && apt-get install -y python3
Используйте инструкцию COPY или ADD, чтобы скопировать файлы или директории из вашей локальной системы внутрь контейнера. Например, чтобы скопировать файл "app.py" из текущей директории внутрь контейнера в директорию "/app/", вы можете написать:


COPY app.py /app/
Установите рабочую директорию с помощью инструкции WORKDIR. Это указывает контейнеру, в какой директории выполнять команды по умолчанию. Например:


WORKDIR /app
Определите команду, которая будет выполняться при запуске контейнера, с помощью инструкции CMD. Эта команда будет выполнена, если при запуске контейнера не указана другая команда. Например, чтобы запустить приложение Python 3, вы можете написать:


CMD ["python3", "app.py"]
При необходимости, вы можете также использовать инструкцию ENTRYPOINT для определения точки входа, которая будет выполняться при запуске контейнера. Эта инструкция обычно используется, чтобы определить исполняемую программу, которая будет запущена, и может комбинироваться с CMD.

После того как вы создали Dockerfile, вы можете собрать Docker-образ с помощью команды docker build. Например:


docker build -t my-docker-image .
После сборки образа, вы можете создать контейнер на его основе с помощью команды docker run. Например:


docker run -it my-docker-image
Это запустит контейнер, и он выполнит команду, указанную в инструкции CMD или ENTRYPOINT.

## Работа с контейнером

docker run: Запускает контейнер из образа.
Пример: docker run my-image

docker start: Запускает остановленный контейнер.
Пример: docker start my-container

docker stop: Останавливает запущенный контейнер.
Пример: docker stop my-container

docker restart: Перезапускает контейнер.
Пример: docker restart my-container

docker pause: Приостанавливает выполнение контейнера.
Пример: docker pause my-container

docker unpause: Возобновляет выполнение приостановленного контейнера.
Пример: docker unpause my-container

docker exec: Запускает команду внутри работающего контейнера.
Пример: docker exec -it my-container bash

docker attach: Присоединяется к работающему контейнеру и подключается к его выводу.
Пример: docker attach my-container

docker logs: Выводит логи контейнера.
Пример: docker logs my-container

![скрин 1](https://github.com/konopleva-nina/Containerization-courseGB/blob/main/Homework4_scrin1.jpg)
![скрин 2](https://github.com/konopleva-nina/Containerization-courseGB/blob/main/Homework4_scrin2.jpg)
![скрин 3](https://github.com/konopleva-nina/Containerization-courseGB/blob/main/Homework4_scrin3.jpg)
![скрин 4](https://github.com/konopleva-nina/Containerization-courseGB/blob/main/Homework4_scrin4.jpg)
![скрин 5](https://github.com/konopleva-nina/Containerization-courseGB/blob/main/Homework4_scrin5.jpg)



