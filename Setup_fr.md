# Nécessaire pour une rasp-effect

- Raspberry-pi 3 et son alimentation
- Carte SD-micro 8 gb
- Carte son USB comme [celle-ci](https://www.amazon.fr/CSL-Surround-dynamique-fonctionnelles-comprises/dp/B00NXUZARM/ref=sr_1_1?s=electronics&amp;ie=UTF8&amp;qid=1473490479&amp;sr=1-1&amp;keywords=carte+son)
- Un écran HDMI, un clavier usb, une souris usb,

# Installation d'une rasp-effect

1. Créer une image raspbian sur la carte microsd comme sur [ce tutoriel](http://raspbian-france.fr/creer-carte-sd-raspberry-raspbian-avec-windows/)
2. Mettre la carte micro-sd dans le rapsberry-pi, brancher l'écran, le clavier et la souris
3. Alimenter le raspeberry-pi et après la fin du démarrage, tapez "pi" comme utilisateur, mot de passe "raspberry"
5. Taper les instructions suivantes pour ccnfigurer le démarrage en mode graphique sans login :
```bash
sudo apt-get update
sudo apt-get upgrade
sudo rapsi-config
```
En se basant sur [cette page] (http://www.framboise314.fr/configurer-la-framboise314-le-premier-demarrage-du-raspberry-pi-il-est-vivant/) pour configurer le démarrage en mode graphique sans mot de passe 

6. Taper les instructions suivantes pour installer «pure-data » :
sudo apt-get install puredata (TODO https://guitarextended.wordpress.com/2013/01/28/rpi-as-guitar-effects-processor-installing-and-configuring-pd/)
```bash
cd Downloads
wget  [http://sourceforge.net/projects/pure-data/files/libraries/mapping/mapping-0.2.1.tar.gz](http://sourceforge.net/projects/pure-data/files/libraries/mapping/mapping-0.2.1.tar.gz)
tar -xvf mapping-0.2.1.tar.gz
sudo mv mapping-0.2.1 /usr/lib/puredata/mapping
```bash
7. Activer le wifi et se connecter à votre wifi en se basant sur [cette page](http://the-raspberry.com/wifi-config)
8. Taper les instructions suivantes pour installer « rasp-guitar »
wget TODO
mkdir /home/pi/Documents/rasp-guitar
cp -R /tmp/rasp-guitar/\* /home/pi/Documents/rasp-guitar
9. Taper les instructions suivantes pour configurer le lancement de « pure-data » et du patch RaspGuitar Autostart
TODO in /home/pi/.config/lxsession/LXDE-pi/autostart, add the line:
@pd /home/pi/Documents/rasp-guitar/RaspGuitar-Autostart.pd
10. Taper les instructions suivantes pour désactiver la mise en veille du wifi
sudo nano /etc/modprobe.d/8192cu.conf
and add the following line :
options 8192cu rtw\_power\_mgnt=0 rtw\_enusbss=