# Gammu

Gammu est le nom du projet et celui de l'utilitaire en ligne de commande qui vous permet de de contrôler votre téléphone. Il est écrit en C et s'appuie sur libGammu.

L'utilitaire en ligne de commande Gammu fournit l'accès à une large gamme de fonctionnalités des téléphones. Cependant le niveau d'intégration diffère d'un téléphone à l'autre et vous voudrez vérifier dans [la base de compatibilité Gammu](https://fr.wammu.eu/phones/) des téléphones les résultats avec différents téléphones. Généralement, les fonctionnalités suivantes ne sont pas supportées :

- Journal d'appels, lancement et gestion d'appels
- Récupération, sauvegarde et envoi de SMS
- Récupération de MMS
- Visualisation, export et import des contacts (depuis des formats standards tels que vCard)
- Visualisation, export et import de calendrier et de tâches (aussi depuis des formats standards tels que vCalendar et iCalendar)
- Récupération d'information du réseau et du téléphone
- Accès au système de fichier du téléphone (à noter que certains téléphones se comportent comme un disque USB et ne sont pas accessibles à traver Gammu)

Dans ce tutoriel, je vais vous expliquer comment installer Gammu sur un serveur Linux. Gammu permet d’envoyer des SMS depuis un Raspberry, un PC sur lequel est tourne une plateforme Linux ou même Windows. Gammu vous permettra de transformer votre serveur en passerelle SMS ou gateway SMS. Il faut bien entendu acheter une clé 3G ou un téléphone compatible. Pour ce tutoriel, j'ai utilisé la configuration suivante :

**OS :** CentOS 7<br/>
**Téléphone :** Nokia E71<br/>
**Transmission :** câble<br/>
**Carte SIM :** Free Mobile

## Installation Gammu

Branchez le Nokia et mettre le mode PC Suite. Vérifier si le mobile est bien détectée par le système et compatible.

```
dmesg | grep tty

[248509.493773] cdc_acm 1-3.2:1.10: ttyACM1: USB ACM device
[248509.494929] cdc_acm 1-3.2:1.12: ttyACM2: USB ACM device
```
```
lsusb | grep -i Nokia

Bus 001 Device 105: ID 0421:00ab Nokia Mobile Phones E71 (PC Suite mode)
```

> Vous pouvez aussi vérifié auparavant si le mobile est compatible avec Gammu ([Lien](https://fr.wammu.eu/phones/))

Ensuite installez Gammu. 

```
sudo yum install gammu
```

Détecter la configuration du mobile pour Gammu.

```
gammu-detect
```

Récupérer la configuration affichée à l’écran pour la mettre dans le fichier **/etc/gammurc**

```
vi /etc/gammurc

[gammu]
device = /dev/ttyACM1
name = Nokia Nokia_E71
connection = at

[gammu1]
device = /dev/ttyACM2
name = Nokia Nokia_E71
connection = at
```

Vérifier que Gammu peut utilisé votre mobile avec la commande suivante :

```
gammu identify

Périphérique       : /dev/ttyACM1
Fabricant            : Nokia
Modèle              : unknown (Nokia E71)
Firmware             : V ICPR71_09w22,29-05-09
IMEI                 : 359357033338121
SIM IMSI             : 208150110052449
```

L’envoi de SMS se fait via l’une des deux commandes suivantes :

```
gammu sendsms TEXT 06xxxxxxxx -text "Ceci est un test."
```
```
echo "Ceci est un test." | gammu --sendsms TEXT 06xxxxxxxx
```
