## Установка arp-scan

```
sudo dnf install arp-scan
```

Для сканирования всех девайсов в локальной сети: 
**(Замена Bitwise SSH Client)**

```
sudo arp-scan --localnet
```

Далее подключаемся к нужному хосту

```
ssh pi@192.168.10.74
```
