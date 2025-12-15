# Docker-Compose
Домашнее задание по теме "Оркестрация группой Docker контейнеров на примере Docker Compose" - Машаев Роман

Задча 1

Ссылка на мой репозиторий на Docker Hub:
https://hub.docker.com/r/mazaich/custom-nginx

Задача 2
![Скриншот изобращения процесса выполнения задания](https://github.com/Mazaich/Docker-Compose/blob/main/Screenshot_2025-12-15_23_31_30.png?raw=true)

Задча 3
![Скриншот изобращения процесса выполнения задания](https://github.com/Mazaich/Docker-Compose/blob/main/Screenshot_2025-12-15_23_41_50.png?raw=true)

Контейнер остановился, потому что сигнал Ctrl-C (SIGINT) был отправлен основному процессу контейнера (nginx), 
который завершил свою работу. Docker контейнеры работают, пока работает их основной процесс.

![Скриншот изобращения процесса выполнения задания](https://github.com/Mazaich/Docker-Compose/blob/main/Screenshot_2025-12-15_23_46_34.png?raw=true)
![Скриншот изобращения процесса выполнения задания](https://github.com/Mazaich/Docker-Compose/blob/main/Screenshot_2025-12-15_23_47_37.png?raw=true)
![Скриншот изобращения процесса выполнения задания](https://github.com/Mazaich/Docker-Compose/blob/main/Screenshot_2025-12-15_23_50_21.png?raw=true)

Изменил порт nginx с 80 на 81 внутри контейнера, но проброс портов с хоста остается 8080:80
Nginx внутри контейнера слушает порт 81, а Docker пытается направить трафик на порт 80
Результат: соединение устанавливается (видно в ss), но nginx не отвечает.

![Скриншот изобращения процесса выполнения задания](https://github.com/Mazaich/Docker-Compose/blob/main/Screenshot_2025-12-16_00_15_45.png?raw=true)

Задача 4
![Скриншот изобращения процесса выполнения задания](https://github.com/Mazaich/Docker-Compose/blob/main/Screenshot_2025-12-16_00_29_43.png?raw=true)

Задача 5

![Скриншот изобращения процесса выполнения задания](https://github.com/Mazaich/Docker-Compose/blob/main/Screenshot_2025-12-16_00_38_39.png?raw=true)

Запустится файл compose.yaml, потому что Docker Compose по умолчанию ищет файлы в следующем порядке:
compose.yaml
compose.yml
docker-compose.yaml
docker-compose.yml

![Скриншот изобращения процесса выполнения задания](https://github.com/Mazaich/Docker-Compose/blob/main/Screenshot_2025-12-16_00_46_01.png?raw=true)
![Скриншот изобращения процесса выполнения задания](https://github.com/Mazaich/Docker-Compose/blob/main/Screenshot_2025-12-16_00_46_44.png?raw=true)
![Скриншот изобращения процесса выполнения задания](https://github.com/Mazaich/Docker-Compose/blob/main/Screenshot_2025-12-16_02_02_55.png?raw=true)
![Скриншот изобращения процесса выполнения задания](https://github.com/Mazaich/Docker-Compose/blob/main/Screenshot_2025-12-16_02_07_21.png?raw=true)
![Скриншот изобращения процесса выполнения задания](https://github.com/Mazaich/Docker-Compose/blob/main/Screenshot_2025-12-16_02_17_35.png?raw=true)
![Скриншот изобращения процесса выполнения задания](https://github.com/Mazaich/Docker-Compose/blob/main/Screenshot_2025-12-16_02_22_53.png?raw=true)
"Found orphan containers" - Docker Compose обнаружил "осиротевшие" контейнеры (task5-portainer-1), которые были созданы предыдущими запусками Compose, но не указаны в текущем файле конфигурации (docker-compose.yaml).
Причина: был удаден  файл compose.yaml, в котором был описан сервис portainer. Теперь остался только docker-compose.yaml, который описывает только сервис registry. 
Контейнер task5-portainer-1 стал "осиротевшим", так как он не принадлежит ни к одному сервису в текущем compose-файле.
Docker Compose предлагает запустить команду с флагом --remove-orphans, чтобы автоматически удалить эти контейнеры.

![Скриншот изобращения процесса выполнения задания](https://github.com/Mazaich/Docker-Compose/blob/main/Screenshot_2025-12-16_02_32_09.png?raw=true)
