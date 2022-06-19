# angart-otus_infra
angart-otus Infra repository

# Подключение к `someinternalhost` в одну команду

Есть 2 способа подключения к удаленному серверу по `ssh` через сервер посредник `ProxyJump` и `ProxyCommand`.
Самый простой и надежный `ProxyJump`, но этот способ доступен только с версии OpenSSH 7.5 и требует поддержки `port forwarding` на сервере посреднике. Далее мы будем использовать `ProxyJump`.

## Добавляем в `ssh config` следующие строки:

```
Host bastion
  Hostname <public ip of bastion vm>
  User <user name>

Host someinternalhost
  Hostname <internal ip of someinternalhost>
  ProxyJump <user name>@bastion
  User <user name>

```

## Теперь можно подключиться к `someinternalhost` коммандой:
```
ssh <user name>@someinternalhost
```


## Манипуляция с `config` выше позволяют выпонять подключение по `alias`

```
ssh someinternalhost
```

# VPN pritunl

```
bastion_IP = 51.250.64.177
someinternalhost_IP = 10.128.0.12
```
