# Exorde-Guide Exorde Participation Module CLI v1.3.1 (Docker) (RUS)

Для начала нужно установить Docker версии не старее `Docker version 20.10.20`

Перед началом работы переходим в папку root:

```
cd /root
```

1. Обновляем индексы пакетов apt с помощью update:

```
sudo apt update
```
2. Устанавливаем набор пакетов, необходимых для доступа к репозиторию Docker по HTTPS:

```
sudo apt install apt-transport-https ca-certificates software-properties-common curl 
```

3. Теперь нужно добавить в apt GPG-ключ для работы с репозиторием Docker. GPG-ключи используются для проверки подписей программного обеспечения. Выполняем эту команду:

```
curl -f -s -S -L https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

4. Добавляем репозиторий Docker в локальный список:

```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
```

5. Ещё раз обновим индекс пакетов:

```
sudo apt update
```

6. Установим докер. Параметры “-y” в автоматическом режиме ответит на все вопросы установщика “Yes”:

```
sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```

7. Проверим статус Docker: статус должен выглядеть так `Active: active (running) since Mon 2022-11-07 11:43:24 UTC; 3h 48min ago` 

```
sudo systemctl status docker
```

## Приступаем к установке и запуску модуля.

1. Перед началом работы переходим в папку root:

```
cd /root
```

2. Создаём папку где будет установлем модуль ExordeModuleCLI:

```
mkdir -v ExordeModuleCLI
```

3. Создаём образ Docker для модуля `exorde-cli`

```
docker build -t exorde-cli . 
```

## Запуск модумя через Docker 

Для запуска в реальном времени используем аргумент `-it`

* Примечание к код:

>`YOUR_MAIN_ADDRESS` - это адресс с кошелька Метамаск "Сеть Ethereum Mainnet", должен быть действительным (желательно новый и пустой).

>`LOGGING` - это уровень обработки логов в модуле:

*

```
docker run -it exorde-cli -m YOUR_MAIN_ADDRESS -l LOGGING
```


