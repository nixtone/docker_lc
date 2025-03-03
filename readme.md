# Docker в целом и Docker для Laravel  

__Описание:__ прохождение курса с канала "Laravel Crative".  

[Источник](https://www.youtube.com/playlist?list=PLd2_Os8Cj3t9Ert8mBlNl1UqwllyP1Tm_)  

## Термины  

__docker image__ - образ  
__docker hub__ - хранилище образов  
__docker container__ - docker контейнер  
__Поднять контейнер__ - запустить  
__Виртуальная машина__ - ОС с ресурсами  


## Ссылки  

[Оф.сайт](https://www.docker.com/)  
[Hub. Хранилище образов](https://hub.docker.com/)  


## Требования  
- Узнать билд Windows (не менее "build 19045"):  
  _"Обновление и безопасность - Информация о сборке ОС и системе - Сборка ОС"_.  
- Включение виртуализации:  
  _"Диспетчер задач - Производительность - Виртуализация: включено"_.  

## Установка  

[Мануал по установке](https://docs.docker.com/desktop/install/windows-install/)

- При установке отмечать WSL2.  
- Скачать и установить "Ubuntu LTS" из "Microsoft Store".  
- В "Desktop Docker" установить WSL интеграцию с "Ubuntu".   
  _"Settings - Resources - WSL integration - вкл Ubuntu - Apply & restart"_  
  Выставить WSL2 по умолчанию  
  _"General - Use the WSL 2 based engine"_ и выполнить команду `wsl.exe --set-default-version 2`, должен быть ответ "Операция успешно завершена.".  
- ПКМ на Docker в трее, убедиться что выставлено "Switch to Windows containers...", может быть выставлено "to Linux".  
- Проверить успешность установки. Выполнить:  
  `docker`, `docker-compose` выдаст справку. Можно еще `docker run hello-world`  


# Установленные образы  

Создается "docker-compose.yml"  

[nginx](https://hub.docker.com/_/nginx)  
[php](https://hub.docker.com/_/php)  

`docker-compose up -d` // запуск сервиса  
Просмотр запущенного nginx: http://localhost:8876/  

"conf.d" общепринятое названия для конфигов  
`docked exec -it nginx-nginx-1 bash` // запуск сервиса от контейнера  
`cd etc/nginx/conf.d/` // увидим общий конфиг  
`docker-compose down` // останавливаем сервис (если обновили yml конфиг и нужно подхватить изменения, потом up)  

### Laravel docker

Иногда отдает ошибку 500, нужно:  
`docker exec -it project-app bash` // в контейнер можно не заходить  
В "/var/www" `php artisan key:generate`  