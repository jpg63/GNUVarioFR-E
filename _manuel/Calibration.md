---
step: 7
description: La calibration
---

**Il est important de calibrer l'accéléromètre**

Le GnuVario-E intégre un accéléromètre, qui doit être calibré.

D'abord sous Windows ou Mac, installez [Python version 2](https://www.python.org/) . Sous Windows, assurez-vous de cocher l'option **add to PATH variable**.
       
Récupérer le code {% include lienfichier.md name="calibration.zip" lien="fichiers/calibration.zip" %} que vous placerez dans un dossier nommé par exemple "best-fit-calibrage"       
      
Copier le fichier {% include lienfichier.md name="variocal.cfg" lien="fichiers/variocal.cfg" %} vierge       
       
Assurez-vous que votre carte SD est à l'intérieur du variomètre.     
         
Passez en mode calibration en appuyant sur le bouton droit au démarrage (au moment de l'écran d'init).          
Vous avez quelques secondes pour placer le vario à plat et appuyer sur le bouton central.       

**Attender les 3 bips** puis commencé à faire pivoter le vario dans toute les directions     
Vous devez faire environ 5 à 6 déplacement par face en attendant le bip entre chaque déplacement    

A la fin, appuyer sur le bouton gauche du vario pour terminer la calibration. Le vario redémarre.       

<iframe width="560" height="315" src="https://www.youtube.com/embed/6yxoZcxxzVY" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

Cela va créé un fichier "RECORD**.CAL" sur la carte SD. Copiez ce fichier dans le dossier "best-fit-calibration" et renommez-le si nécessaire en tant que "RECORD00.IGC".

Sous Windows ou Mac, lancez l'**Idle** Python et ouvrez le programme "best-fit-calibrage/calibrer.py". Appuyez sur "F5" pour exécuter.

Sous Linux, lancez simplement :

{% highlight shell_session %}
~$ cd Arduino/best-fit-calibration
~/best-fit-calibration$ python2 calibrate.py
{% endhighlight %}

Cela montrera les paramètres que vous devez remplacer dans votre fichier *HardwareConfig.h* (utile si pas de sdcard, mais nécessite une compilation) et *variocal.cfg* ou recopier sur la page Web de configuration

