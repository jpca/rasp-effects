# Installation d'une rasp-effect

# Pré-requis

- 1 Raspberry-pi 3 et son alimentation
- 1 Carte SD-micro 8 gb
- 1 Carte son USB comme [celle-ci](https://www.amazon.fr/CSL-Surround-dynamique-fonctionnelles-comprises/dp/B00NXUZARM/ref=sr_1_1?s=electronics&amp;ie=UTF8&amp;qid=1473490479&amp;sr=1-1&amp;keywords=carte+son)
- 1 écran HDMI, un clavier usb, une souris usb pour la configuration et les changements
- 2 cables jack 3.5 male-male (l'un de moins d'1m et l'autre de plus de 2m)  
- 1 adaptateur jack male 3.5 - 6.15

## Pour une installation montée sur une guitare
- 1 batterie usb 2.1A
- un système de fixation adhoc 

# Installation

1. Créer une image raspbian sur la carte microsd comme sur [ce tutoriel](http://raspbian-france.fr/creer-carte-sd-raspberry-raspbian-avec-windows/)

2. Mettre la carte micro-sd dans le rapsberry-pi, brancher l'écran, le clavier et la souris

3. Alimenter le raspeberry-pi et après la fin du démarrage, tapez "pi" comme utilisateur, mot de passe "raspberry"

5. Taper les instructions suivantes pour ccnfigurer le démarrage en mode graphique sans login :
```bash
sudo apt-get update
sudo apt-get upgrade
sudo rapsi-config
```
6. Se baser sur [cette page] (http://www.framboise314.fr/configurer-la-framboise314-le-premier-demarrage-du-raspberry-pi-il-est-vivant/) pour configurer le démarrage en mode graphique sans mot de passe 

7. Taper les instructions suivantes pour installer pure-data :
```bash
sudo apt-get install puredata
cd
cd Downloads
wget  [http://sourceforge.net/projects/pure-data/files/libraries/mapping/mapping-0.2.1.tar.gz](http://sourceforge.net/projects/pure-data/files/libraries/mapping/mapping-0.2.1.tar.gz)
tar -xvf mapping-0.2.1.tar.gz
sudo mv mapping-0.2.1 /usr/lib/puredata/mapping
```

8. Activer le wifi et se connecter à votre wifi en se basant sur [cette page](http://the-raspberry.com/wifi-config)

9. Taper les instructions suivantes pour installer les effets
```bash
wget https://github.com/jpca/rasp-effects/archive/master.zip
unzip master.zip
mkdir /home/pi/Documents/rasp-effects
cp rasp-effects-master/raspberry/patches/*.pd /home/pi/Documents/rasp-effects
```

10. Taper les instructions suivantes pour lancer pure-data et un patch au démarrage
```bash
cat <<EOT >> /home/pi/.config/lxsession/LXDE-pi/autostart
@pd /home/pi/Documents/rasp-effects/RaspGuitar-WhaAuto.pd
EOT
```

10. Taper les instructions suivantes pour désactiver la mise en veille du wifi
```bash
sudo cat <<EOT >> /etc/modprobe.d/8192cu.conf
options 8192cu rtw\_power\_mgnt=0 rtw\_enusbss=
EOT
```
