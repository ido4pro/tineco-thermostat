# Tineco


## Hardware


Tineco est un thermostat connecté en wifi pour piloter une chaudière ou un radiateur électrique.

![electronic board](images/electronic-board-small.png)

Tineco est basé sur la puce ESP8266 qui dispose d'un kit de développement permettant de personnaliser facilement son firmware.

Tineco dispose d'une sonde de température et d'un relai 10 A avec un capteur de mesure du courant consommé.

Tineco s'auto-alimente à travers son entrée 220v à travers un convertisseur AC/DC intégré.

Le software de l'ESP8266 est surveillé par un watchdog matériel qui le reset lorsqu'il ne donne plus signe de vie.

![hardware](images/tineco-hardware.png)

![esp8266](images/esp8266-core.png)

![power](images/power-AC-DC.png)

![temperature humidity sensor](images/tem-hum-sensor.png)

![one wire bus](images/one-wire-bus.png)

![relay with current sensor](images/relay-with-current-sensor.png)

![power](images/zero-detection.png)

![power](images/current-input.png)


## Software


Les codes sources de Tineco s'appuie sur le framework [sming](https://github.com/SmingHub) et le language C++. 

Ils seront prochainement mis à disposition.

## Setting

Tineco embarque une page web qui permet de paramétrer la connexion WIFI à utiliser.  

## API

###Tineco se pilote par des requêtes HTTP

1. Allumer le relai : http://ipDeTineco/api/?set=relay&value=on
2. Eteindre le relai : http://ipDeTineco/api/?set=relay&value=off
3. Lire l'état du relai : http://ipDeTineco/api/?get=relay
4. Lire la température : http://ipDeTineco/api/?get=temperature
5. Lire le courant : http://ipDeTineco/api/?get=current
6. Lire l'identifiant unique de l'ESP8266 : http://ipDeTineco/api/?get=uniqueId

###Tineco se pilote aussi à travers le procotocole [mqtt](http://www.mqtt.org/)

Par défaut, tineco écoute le topic 'tineco/xxxx(UniqueId)/in' et répond sur le topic 'tineco/xxxx(UniqueId)/out'

1. Allumer le relai : "tineco/xxxx(UniqueId)/in" {'set':'relay','value'='on'} / "tineco/xxxx(UniqueId)/out/set" -> {'value':'apply'}
2. Eteindre le relai : "tineco/xxxx(UniqueId)/in" {'set':'relay','value'='off'} / "tineco/xxxx(UniqueId)/out/set"  -> {'value':'apply'} 
3. Lire l'état du relai : "tineco/xxxx(UniqueId)/in" {'get':'relay'} / "tineco/xxxx(UniqueId)/out/relay"  -> {'value':'off'} ou {'value':'on'}
4. Lire la température : "tineco/xxxx(UniqueId)/in" {'get':'temperature'} / "tineco/xxxx(UniqueId)/out/relay/temperature"  -> {'value':'18.6'}
5. Lire le courant : "tineco/xxxx(UniqueId)/in" {'get':'current'} / "tineco/xxxx(UniqueId)/out/relay/current"  -> {'value':'on'}




 
 
 




