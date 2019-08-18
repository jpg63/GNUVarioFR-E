---
layout: page
title: Schémas
linkdesc: Le schéma de câblage du GNUVario
linkmsg: Trouver !
linktarget: "/assets/schematic.pdf"
---

Cette page explique comment assembler les composants GNUVario-E par vous-même. Si vous utilisez le circuit imprimé du GNUVario-E, vous pouvez aller directement à la page [Construction]({{ site.baseurl }}{% link hardware.md %}).

De quoi avez-vous besoin :
--------------

Presque tous les composants sont optionnels sauf un ESP32 et un ms5611. Vous pouvez vous adapter à vos besoins. Vous devez simplement éditer le fichier libraries / HardwareConfig / HardwareConfig.h et désactiver le composant que vous n'avez pas.

Par exemple, si vous n'avez que le haut-parleur, l'écran et le diviseur de tension, modifiez le fichier comme suit:

{% highlight c %}
/* Commenter ou décoummenter selon  */
/* ce que vous intégrez dans le variomètre  */ 
#define HAVE_SPEAKER
//#define HAVE_ACCELEROMETER
#define HAVE_SCREEN
//#define HAVE_GPS
//#define HAVE_SDCARD
//#define HAVE_BLUETOOTH
#define HAVE_VOLTAGE_DIVISOR
{% endhighlight %}


Donc vous avez besoin ou vous pouvez obtenir :
* Une carte ESP32 (de préférence TTGO-T5 v1.2)
* Une carte ms5611 ( peut être combinée avec l'accéléromètre MPU9250 )
* Une carte MPU9250 ( peut être combinée avec le baromètre ms5611 )
* Un Haut-Parleur (intégré à la board TTGO-T5)
* Un écran E-Paper waveshare 1.54'' (intégré à la board TTGO-T5)
* Un module GPS (de préférence ATGM336H)
* Un module lecteur de carte SD (intégré à la board TTGO-T5)
* Une résistance 270k et 1M pour le diviseur de tension
* Deux résistances 1k pour le pull-up du MS5611
* Une résistance 1k et un transistor S8050 ou équivalent (2N2222) pour la commande de l'alimentation des cartes



Câblage du variomètre :
---------------------

Vous avez maintenant votre source d'alimentation **5V** qui fournit plus de 3,3 v et une source d'alimentation régulée **3,3 v**. Vous pouvez maintenant connecter tous les composants suivant ce [schéma]({{"/assets/schematic.pdf" | absolute_url}}) ou le tableau ci-dessous. **Attention** les numéros de broches ne sont valables que pour le TTGO-T5 V1.2.

**The ms5611 and MPU9250 board**

|    ms5611 board  |     TTGO-T5    |  
| :--------------: | :------------: |
|       SDA        |        21      |
|       SCL        |        22      |
|       VCC        |       3.3v     |
|       GND        |       GND      |

**haut parleur** 

|          HP          |     TTGO-T5    |  
| :------------------: | :------------: |
|       +              |       25       |
|       -              |       GND      |

**Ecran E-Paper waveshare 1.54''**

|    Ecran         |     TTGO-T5          |  
| :--------------: | :------------------: |
|       SCK        |  14                  |
|     DIN/MOSI     |  15                  |
|      MISO        |  2                   |
|       DC         |  GPIO 17             |
|       CS         |  GPIO 5              |
|       RST        |  GPIO 16             |
|       VCC        |  3.3v régulé         |
|       GND        |  GND                 |
|      BUSY        |  GPIO 4              |

**Lecteur carte SD**

|    SD card         |     TTGO-T5         |  
| :----------------: | :-----------------: |
|       CS           |   13                |
|       MOSI         |   15                |
|       MISO         |   2                 |
|       SCLK         |   14                |
|     5v or 3.3v     |   3.3v régulé       |
|       GND          |   GND               |

**Carte GPS**

|    carte GPS     |     Arduino                          |  
| :--------------: | :----------------------------------: |
|       TX         |        19                            |
|       RX         |    Tout (pas utilisé actuellement)   |
|       VCC        |       3.3v                           |
|       GND        |       GND                            |


**Diviseur de tension** (270k et 1M résistances en ligne)

|    diviseur de tension       |     TTGO-T5      |  
| :--------------------------: | :--------------: |
|       Côté 270k              |     Batterie +   |
|       Entre les résistances  |     35           |
|       Côté 1M                |     GND          |
                    
										
**LED** 

|       Led                    |     TTGO-T5      |  
| :--------------------------: | :--------------: |
|                              |     22           |


**Boutons** 

|       Bouton                 |     TTGO-T5      |  
| :--------------------------: | :--------------: |
|       Bouton A               |     38           |
|       Bouton B               |     37           |
|       Bouton C               |     39           |















 

