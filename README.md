# devops-1
Практическое задание по занятию "Оркестрация группой Docker контейнеров на примере Docker Compose."

# Задание 1

https://hub.docker.com/repository/docker/francothedwarf/custom-nginx/general

# Задание 2

![Ответ на задание 2](https://github.com/Francotirado/devops-1/blob/main/img/2.jpg)

# Задание 3

Нажав комбинацию клавиш Ctrl+C во время выполнения команды docker attach мы отправили контейнеру сигнал SIGINT, который прерывает процесс работы контейнера и приостанавливает его

Так как мы сменили порт, который по стандарту слушает nginx внутри контейнера на 81, а вне его у нас установлено проксирование запроса хостового порта 8080 на порт 80 внутри контейнера, то мы получили ошибку соединения, так как по указанному маршруту ничего нет.

![Ответ на задание 3-1](https://github.com/Francotirado/devops-1/blob/main/img/3-1.jpg)

![Ответ на задание 3-2](https://github.com/Francotirado/devops-1/blob/main/img/3-2.jpg)

![Ответ на задание 3-3](https://github.com/Francotirado/devops-1/blob/main/img/3-3.jpg)

# Задание 4

![Ответ на задание 4](https://github.com/Francotirado/devops-1/blob/main/img/4.jpg)

# Задание 5

Запустится файл compose.yaml так как по официальной документации - это стандартный файл для запуска docker-compose

Так как мы удалили манифест, откуда запускается контейнер, но не сам контейнер, то он остался работать. Поэтому выводится предупреждение о том, что можно удалить оставшиеся контейнеры добавив к команде docker compose up -d параметр --remove-orphans

Содержимое compose.yaml:

```
version: "3"
include:
  - docker-compose.yaml
services:   
  portainer:
    network_mode: host
    image: portainer/portainer-ce:latest
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock

```

![Ответ на задание 5-1](https://github.com/Francotirado/devops-1/blob/main/img/5-1.jpg)

![Ответ на задание 5-2](https://github.com/Francotirado/devops-1/blob/main/img/5-2.jpg)
