# vault-cluster

Запуск Vault Cluster через docker-compose.

После запуска необходимо выполнить инициализацию на любом из узле кластера (в примере узел 1).

```shell
vault operator init
```

Вы получите  Unseal Key и Initial Root Token.

```shell
Unseal Key 1: yPb4YqTEOHMGoHhyOoRfAy64i80i6tl6JS1w9dRLaWgR
Unseal Key 2: DbXY5ZL06ekUwj/uBQielhhRFUYU2/22j+Aroot/2xEZ
Unseal Key 3: 3sghpmojskMwnNPocxoGrSbXgd2Pw6p3s+g0tivTP7Wi
Unseal Key 4: jymiORUThAmsGyxZIP64ZQR2LOZTx19ocTdS+LvtUrr1
Unseal Key 5: ojmrHfkutoJG0Nwn9CQXMl8rg4Bp5PkwFhILmMNndPyX

Initial Root Token: hvs.xFLOGRtAFog8FWPg9G8v7sGu
```
Сохраните их в безопасное место.

Затем выполните 3 раза команду:

```shell
vault operator unseal
```
И введите три любые (разные) Unseal Key (например Unseal Key 1, Unseal Key 4, Unseal Key 2)  

# Добавление нод в кластер

Далее на оставшихся нодах выполните:

```shell
vault operator raft join http://vault1:8200
```
```shell
vault operator unseal
```
Последнюю команду требуется выполнить 3 раза и ввести три любых (разных) Unseal Key (например Unseal Key 1, Unseal Key 4, Unseal Key 2).


<img width="1160" alt="image" src="https://github.com/user-attachments/assets/d7268456-89c9-4e9f-8c02-f63106e380f1" />


