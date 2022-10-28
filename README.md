# Rapport-TP-reseau

## TP1

### 1.3.4.2) IfConfig et ping sur le Routeur

IP du routeur : 192.168.106.177

![image](https://user-images.githubusercontent.com/73313152/198582166-33af5d1b-54d1-4dd0-a340-3441131246d7.png)

![image](https://user-images.githubusercontent.com/73313152/198582421-6f5cbde7-fffd-4099-9b28-5d2c53adcf72.png)

### 1.3.4.3) Affichage /etc/hosts

![image](https://user-images.githubusercontent.com/73313152/198583386-b33a82a2-4417-4d0d-a9a4-0479cc0b990b.png)

### 1.6.1) If Config

Les 3 cartes réseaux ont bien étaient créées.

![image](https://user-images.githubusercontent.com/73313152/198586749-969bbfa6-ce09-4f42-9a35-687849c4acf8.png)

### 1.6.2) Table Routage Routeur

![image](https://user-images.githubusercontent.com/73313152/198589356-982d79b3-1aae-451d-a54f-287a46bdcaa9.png)

### Table Routage Host1

![image](https://user-images.githubusercontent.com/73313152/198592810-c1c17b6c-6a42-49bd-bcbb-24ae88862992.png)

### Table Routage Host2

![image](https://user-images.githubusercontent.com/73313152/198594707-1b30d594-5b92-455c-be74-dccab3de120f.png)

### 1.9.4 Activation IPForwarding
![image](https://user-images.githubusercontent.com/73313152/198607935-507b19fb-8db7-4bce-951a-b58524aff189.png)

IP Forwarding est le procédé qui fait le routage internet, il  va permettre de déterminer la direction du réseau où les paquets IP, les datagrammes peut être envoyé (routage IP).

L'ip forwarding va spécifier au routeur de faire passer les paquets qui ne lui sont pas adréssés.
### 1.10.1 Activation de Mascarade 

Afin de pouvoir ping 8.8.8.8 depuis host1 nous avons du activer Mascarade afin de faire en sorte que l'adresse du routeur puisse etre mis sur le paquet de host1 envoyé sur internet

![image](https://user-images.githubusercontent.com/73313152/198615623-be299c06-39c8-443d-b19c-56c897b5b64a.png)

## TP2

### Config routeur 1

```sh
 
 ipR2 = '172.30.0.2'
 ipR3 = '172.40.0.2'
 networkHost3 = '172.60.0.0\16'
 networkHost4 = '172.70.0.0\16'
  
 ## Route classique
 ip route add $networkHost3 via $ipRouteur2 metric 500
 ip route add $networkHost4 via $ipRouteur3 metric 500
 
 ## Route de Secours
 
 ip route add $networkHost3 via $ipRouteur3 metric 1000
 ip route add $networkHost4 via $ipRouteur2 metric 1000
 
 ```
### Config routeur 2

```sh

 ipR1 = '172.30.0.2'
 ipR3 = '172.50.0.2'
 networkHost1 = '172.10.0.0\16'
 networkHost2 = '172.20.0.0\16'
 networkHost4 = '172.70.0.0\16'
  
 ## Route classique
 ip route add $networkHost1 via $ipRouteur2 metric 500
 ip route add $networkHost2 via $ipRouteur1 metric 500
 ip route add $networkHost4 via $ipRouteur3 metric 500
 
 ## Route de Secours
 
 ip route add $networkHost1 via $ipRouteur3 metric 1000
 ip route add $networkHost2 via $ipRouteur3 metric 1000
 ip route add $networkHost4 via $ipRouteur1 metric 1000

```

### Config routeur 3

```sh

 ipR1 = '172.40.0.2'
 ipR2 = '172.50.0.2'
 networkHost1 = '172.10.0.0\16'
 networkHost2 = '172.20.0.0\16'
 networkHost3 = '172.60.0.0\16'
  
 ## Route classique
 ip route add $networkHost1 via $ipRouteur1 metric 500
 ip route add $networkHost2 via $ipRouteur1 metric 500
 ip route add $networkHost3 via $ipRouteur2 metric 500
 
 ## Route de Secours
 
 ip route add $networkHost1 via $ipRouteur2 metric 1000
 ip route add $networkHost2 via $ipRouteur2 metric 1000
 ip route add $networkHost3 via $ipRouteur1 metric 1000
 
 ```
