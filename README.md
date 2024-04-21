# ProjectAndroidCamera - BLASCO Basile & AGENEAU William IR5CP

### 1 - Objectif de l'application

Cette application Android a pour but de récupérer le fulx vidéo du téléphone sur lequel elle est installée. L'application peut récupérer les images de la caméra principale ainsi que de la caméra frontale en fonction du choix de l'utilisateur à l'aide du bouton "FLIP".

Le flux vidéo va ensuite être envoyé vers un serveur distant auquel l'application se connecte via TCP/IP afin d'ouvrir une communication qui servira à envoyer le flux vidéo. Le flux est envoyé sous formes d'images encodées au type H264 qui sont envoyées à intervalle réguliers et qui une foi décodée par le serveur sont assemblées afin de créer la vidéo.

### 2 - Fonctionnalités supplémentaires envisagées

Après avoir obtenu une version stable de l’application nous permettant d’envoyer le flux vidéo du téléphone sur le serveur nous avons essayé d’implémenter différentes fonctionnalités.  

Premièrement l’envoi du flux vidéo vie RTSP ou WebRTC pour cela nous avons essayé d’utiliser différentes librairies externes ou comprise dans OpenCV mais les librairies ne se compilaient pas ou entraient en conflit avec les autres parties du code déjà existant de l’application. Nous avons ensuite essayé d’envoyer le flux audio en même temps que le flux vidéo au serveur à l’aide de la librairie OpenSL ES mais une fois de plus la librairie ne se compilait et entrait en conflit avec les parties existantes du code. 

Nous avons essayé d’adapter le code existant aux librairies mais comme ce n’était pas notre code nous avons eu beaucoup de mal à le comprendre et nos modifications 

Une autre fonctionnalité envisagée était de retirer le filtre bleuté qui s'applique à l'image lors de l'encodage et du décodage. Notre meilleure tentative a résulté en la moitié de l'écran de la bonne couleur et l'autre moitié uniquement de la couleur verte ce qui n'était pas concluant pour être implémenté.

### 3 - Fonctionnalités implémntées

Pour les fonctionnalités développées nous avons collaborés avec le groupe de Joris Vinet et Gauthier Perrault afin de pouvoir produire un seul code amélioré implémentant des fonctions de traitement d'images

#### Détection des bords

La fonction de détection des bords va analyser les changements d'intensité lumineuse afin de déterminer les contours des objets présents à l'image qui seront donc mis en évidence par une surbrillance.

![Edge Detect](https://github.com/BlascoBasile/ProjectAndroidCamera/assets/94351884/26b08af2-84ca-439f-9781-3936d8cb6fc7)

#### Fonction de floutage

La fonction de floutage permet de rendre floue l'image envoyée au serveur distant par un flou Gaussien.

![BlurCompare](https://github.com/BlascoBasile/ProjectAndroidCamera/assets/94351884/c0d0a564-4a47-4bd2-8dce-37386b3e7984)

#### Fonction de Zoom

La fonction de zoom va agrandir le centre de l'image sur le serveur selon un ZoomFactor à renseigner dans le code.

![ZoomCompare](https://github.com/BlascoBasile/ProjectAndroidCamera/assets/94351884/71b9348a-34ff-45d3-a79e-b11c2ee8d60c)

#### Fonction d'inversion des couleurs

La fonction d'inversion des couleurs va appliquer un flitre négatif sur les couleurs de l'image affichée sur le serveur.

![InvertCompare](https://github.com/BlascoBasile/ProjectAndroidCamera/assets/94351884/6d9d6ba3-9640-4a57-8c8a-99c6f9f6c6ef)




