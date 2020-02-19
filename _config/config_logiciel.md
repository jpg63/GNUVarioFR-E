---
step: 2
description: La configuration logiciel
---

Il existe 3 méthodes pour configurer votre variomètre avec vos paramètres personnels

a) La page Web

Le plus simple pour configurer votre GnuVario-E est d'utiliser la page web embarquée et le mode Wifi.  
Ceci va mettre à jour automatiquement les fichiers de configuration sur la sdcard.
Cette fonctionnalitée est décrite dans le [manuel d'utilisation]({{ site.baseurl }}{% link 7-manuel.md %}).

b) Les fichiers de configuration sur la carte SD.

Ces fichiers se trouvent à la racine de la carte SD ; ils sont décrits plus en détail en bas de cette page.  
Ils permettent de configurer le GNUVario sans avoir à recompiler le code.
- params.jso : contient les paramètres généraux du GNUVario.
- wifi.cfg : contient les informations de connexion au réseau wifi ; on peut déclarer jusqu'à 4 réseaux wifi différents.
- variocal.cfg : contient les informations de calibration du GNUVario. Voir le [manuel d'utilisation]({{ site.baseurl }}{% link 7-manuel.md %}) pour l'opération de calibration.

c) Le fichier VarioSettings.h

Cette méthode est réservée aux utilisateurs confirmés qui souhaite utiliser du matériel non standard ou recompiler le code

Si vous ne souhaitez pas utiliser de carte SD, vous pouvez modifier le fichier libraries/VarioSettings/VarioSettings.h afin de personnaliser votre vario. L'utilisation de ce fichier nécessite la recompilation du code

[libraries/VarioSettings/VarioSettings.h](https://github.com/jpg63/Gnuvario_for_TTGO-T5/blob/master/Sources/Stable%20Code/libraries/VarioSettings/VarioSettings.h)
