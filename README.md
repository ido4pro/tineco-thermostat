# Tineco


## Hardware


Tineco est un thermostat wifi pour radiateur électrique basé la puce ESP8266.

Tineco pilote le radiateur à travers un relai 10 ampères.

Tineco dispose d'une sonde de température et d'un capteur de mesure du courant consommé par le radiateur.

Tineco s'auto-alimente à travers un convertisseur AC/DC.

Le software de Tineco est surveillé par un watchdog matériel qui relance Tineco lorsqu'il ne donne plus signe de vie.

![hardware](images/tineco-hardware.png)

## Software


Les sources de Tineco s'appuie sur le framework [sming](https://github.com/SmingHub)

## Setting

Tineco embarque une page web qui permet de paramétrer la connexion WIFI à utiliser.  

## API

Tineco se pilote par des requêtes HTTP

1: Allumer le relai : http://ipDeTineco/api/?cmd=relay&state=ON
2: Eteindre le relai : http://ipDeTineco/api/?cmd=relay&state=OFF
3: Lire l'état du relai : http://ipDeTineco/api/?cmd=readRelay
4: Lire la température : http://ipDeTineco/api/?cmd=readTemperature
5: Lire le courant : http://ipDeTineco/api/?cmd=readCurrent

Tineco se pilote aussi à travers le procotocole [mqtt](http://www.mqtt.org/)
 
 
 




