# EscalierMusical



La ligne 56 sensors[i].setAddress(0x30 + i); définit l'adresse I2C pour chaque capteur laser VL53L0X dans le tableau sensors.

Le protocole I2C est utilisé pour communiquer avec plusieurs périphériques sur un même bus, et chaque périphérique doit avoir une adresse unique pour permettre une communication correcte. Par défaut, tous les capteurs VL53L0X ont la même adresse I2C, ce qui peut entraîner des conflits lors de l'utilisation de plusieurs capteurs sur un même bus I2C.

La fonction setAddress() modifie l'adresse I2C du capteur pour éviter ces conflits. Dans cette ligne de code, l'adresse de base 0x30 est ajoutée à la valeur de i, qui varie de 0 à (NUM_SENSORS - 1). Ainsi, chaque capteur aura une adresse unique dans la plage de 0x30 à 0x30 + (NUM_SENSORS - 1).

Cette configuration permet à l'Arduino de communiquer individuellement avec chaque capteur VL53L0X et de lire les données de distance de chaque capteur sans interférence.
