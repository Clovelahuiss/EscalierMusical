# EscalierMusical

Ce Github a été créé pour un projet appelé "Escalier musical". Le but de ce projet est de jouer de la musique et d'animer des LEDs lorsqu'une personne monte ou descend un escalier. Pour cela, le programme utilise des capteurs laser VL53L0X, un module RTC_DS3231 pour la gestion du temps, un module DFPlayer Mini pour la lecture de fichiers audio et des LEDs WS2812B pour l'animation lumineuse.

Le code commence par inclure les bibliothèques nécessaires et définir les constantes pour la configuration des LEDs, des broches, du nombre de capteurs laser et des seuils de distance. Ensuite, il déclare plusieurs tableaux de notes pour différentes mélodies et initialise la séquence de notes par défaut.

Dans la fonction setup(), le code initialise les différents éléments (capteurs laser, DFPlayer Mini, RTC, LEDs) et règle la luminosité des LEDs. Il vérifie également si le module RTC a perdu l'alimentation et, si c'est le cas, demande de régler l'heure.

Dans la boucle principale (loop()), le code vérifie d'abord l'heure et la date actuelles et met à jour la séquence de notes en fonction de certaines conditions (par exemple, si c'est Noël, jouer "Jingle Bells", si c'est un anniversaire, jouer "Joyeux Anniversaire"). Ensuite, il vérifie si les capteurs détectent la présence d'une personne sur les marches de l'escalier. Si une détection a lieu, le code appelle une fonction pour animer les LEDs en fonction de la marche sur laquelle la personne se trouve.

Enfin, si la détection a lieu et qu'un certain délai s'est écoulé depuis la dernière note jouée, le code joue la note suivante de la séquence et met à jour les variables de détection et d'index de note. Il gère également les situations où la personne monte ou descend l'escalier et adapte les animations et les sons en conséquence.



EXPLICATION DU CODE : 




La ligne 56 sensors[i].setAddress(0x30 + i); définit l'adresse I2C pour chaque capteur laser VL53L0X dans le tableau sensors.

Le protocole I2C est utilisé pour communiquer avec plusieurs périphériques sur un même bus, et chaque périphérique doit avoir une adresse unique pour permettre une communication correcte. Par défaut, tous les capteurs VL53L0X ont la même adresse I2C, ce qui peut entraîner des conflits lors de l'utilisation de plusieurs capteurs sur un même bus I2C.

La fonction setAddress() modifie l'adresse I2C du capteur pour éviter ces conflits. Dans cette ligne de code, l'adresse de base 0x30 est ajoutée à la valeur de i, qui varie de 0 à (NUM_SENSORS - 1). Ainsi, chaque capteur aura une adresse unique dans la plage de 0x30 à 0x30 + (NUM_SENSORS - 1).

Cette configuration permet à l'Arduino de communiquer individuellement avec chaque capteur VL53L0X et de lire les données de distance de chaque capteur sans interférence.
