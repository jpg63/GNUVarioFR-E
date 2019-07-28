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
* Un module GPS 
* Un module lecteur de carte SD (intégré à la board TTGO-T5)
* Une résistance 270k et 1M pour le diviseur de tension
* Deux résistances 1k pour le pull-up du MS5611
* Une résistance et un transistor équivalent à un 2N2222 pour la commande de l'alimentation des cartes



Câblage du variomètre :
---------------------

Vous avez maintenant votre source d'alimentation **RAW_V** qui fournit plus de 3,3 v et une source d'alimentation régulée **3,3 v**. Vous pouvez maintenant connecter tous les composants suivant ce [schéma] ({{"/assets/schematic.pdf" | absolute_url}}) ou le tableau ci-dessous. **Attention** les numéros de broches ne sont valables que pour les Arduino basés sur la puce Atmega328 (P).

**The ms5611 and MPU9250 board**

|    ms5611 board  |     Arduino    |  
| :--------------: | :------------: |
|       SDA        |     SDA (A4)   |
|       SCL        |     SCL (A5)   |
|       VCC        |       RAW_V    |
|       GND        |       GND      |

**haut parleur ou buzzer** (sans amplificateur)

|     Buzzer           |     Arduino    |  
| :------------------: | :------------: |
|  + -> résistance 120k|       D9       |
|       -              |       D10      |

**Haut parleur ou buzzer** (Avec un amplificateur L9110, voir [datasheet](https://www.elecrow.com/download/datasheet-l9110.pdf) )

|      Buzzer      |      L9110     |  
| :--------------: | :------------: |
|        +         |       OA       |
|        -         |       OB       |

**Amplificateur L9110** (voir [datasheet](https://www.elecrow.com/download/datasheet-l9110.pdf) )

|      L9110       |      Arduino   |  
| :--------------: | :------------: |
|        IA        |       D9       |
|        IB        |       D10      |
|        VCC       |       RAW_V    |
|        GND       |       GND      |


**Ecran Nokia 5110**

|    Ecran 5110    |     Arduino                              |  
| :--------------: | :--------------------------------------: |
|       SCK        |    SCK (D13)                             |
|     DIN/MOSI     |    MOSI (D11)                            |
|       DC         | Situé dans VarioSettings.h ( defaut D4 ) |
|       CS         | Situé dans VarioSettings.h ( defaut D3 ) |
|       RST        | Situé dans VarioSettings.h ( defaut D2 ) |
|       VCC        |     3.3v régulé                          |
|       GND        |      GND                                 |

**Lecteur carte SD**

|    SD card         |     Arduino                                  |  
| :----------------: | :------------------------------------------: |
|       CS           |  Situé dans VarioSettings.h ( defaut A0 )    |
|       MOSI         |      MOSI (D11)                              |
|       MISO         |      MISO (D12)                              |
|       SCLK         |      SCK (D13)                               |
|     5v or 3.3v     |    RAW_V ou 3.3v régulé                      |
|       GND          |         GND                                  |

**Carte GPS**

|    carte GPS     |     Arduino                          |  
| :--------------: | :----------------------------------: |
|       TX         |        RX                            |
|       RX         |    Tout (pas utilisé actuellement)   |
|       VCC        |       RAW_V                          |
|       GND        |       GND                            |

**Bluetooth module**

|    Bluetooth     |     Arduino                                     |  
| :--------------: | :---------------------------------------------: |
|       RX         |       TX                                        |
|       TX         |     Toute broche avec des interruptions         |
|                  |     (non utilisée actuellement)                 | 
|       VCC        |       RAW_V                                     |
|       GND        |       GND                                       |

**Diviseur de tension** (270k et 1M résistances en ligne)

|    diviseur de tension       |     Arduino                              |  
| :--------------------------: | :--------------------------------------: |
|       Côté 270k              |       Batterie + (RAW_V)                 |
|       Entre les résistances  | Situé dans VarioSettings.h ( defaut A2 ) |
|       Côté 1M                |       GND                                |
                      

















 

