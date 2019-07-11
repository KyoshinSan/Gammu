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

**OS :** CentOS 7

**Téléphone :** Nokia E71

**Transmission :** câble

**Carte SIM :** Free Mobile
