# Bienvenue sur le Projet SAÉ-4: Essaim de Drones dans l'Espace



## Equipe : WEIGEL Léon - POULIN Loup - JAFFEUX Louis
## Enseignant Référents : M. HUEBER Eric - MOURLION Benjamin

### Merci à : BADER Alexandre - TRAN Kevin - KLEINKLAUS Romain - MAYABA Aklaa
> lien vers leurs GitHub : [DronesSAÉ4-2023](https://github.com/arduilex/SAE4_drone?tab=readme-ov-file)

# **SAÉ4 :**

# Sommaire :
1. Récuperation du projet existant
2. Compréhension du projet existant
3. Définition d'un cahier des charges précis et d'un diagramme de GANTT
4. Communiquer avec un drone
5. Communiquer avec les balises de localisation


# **1 : Récuperation du projet existant**
  La récupération du projet existant passe déja pas la récupération du GitHub du projet de l'année dernière. La lecture de leur traces écrites sur ce qu'ils avaient accompli. Ensuite un inventaire du materiel. On compte donc :
  8 balises de localisation, dont une défectueuse. 
  8 drones pilotables, dont un abimé.
  Des batteries portables pour alimenter les balises.
  Un PC sous linux pour l'utilisation du client

# **2 : Compréhension du projet existant**
  Le projet déja existant consiste en un dossier de plusieurs script python, ces scripts ne sont pas annoter, on peut se fier uniquement au nom du script pour deviner leur utilité.
  Aussi le READ ME n'explique pas la procédure de mise en fonctionnement du projet, il faudra donc reprendre le projet de 0. On sait que l'ancien groupe a réussi a localiser les drones dans l'espace ce qui est la finalité du projet.

# **3 : Définition d'un cahier des charges précis et d'un diagramme de GANTT**
  On a du essayer de hierarchisé les differentes tâches a effectuer. N'ayant pas de consigne précise on a pour objectif d'accomplir ces tâches les une après les autres le plus loin possible.
  
![alt tag](https://github.com/SAE3L/DroneSAE4/blob/main/Organisation/Gantt.PNG)

# **4 : Communiquer avec un drone**
  On a réinstaller les differentes librairies proposé par crazyflie. Grace a elle on a réussi a executer du code python, qui grace au librairie peut se connecter aux drones.
  Apres quelques essais ont arrive a récuperer l'orientation des drones, leurs rotations sur les 3 axes. On a donc une partie code qui se connecte avec l'antenne au drone, et une partie qui récupère ces inforlations en temps réelle.
  Le script python ne peut pas s'executer en même temps que l'application client.

![alt tag](https://github.com/arduilex/SAE4_drone/blob/main/images/overview_clientsoftware.jpg?raw=true)

# **5 : Communiquer avec les balises de localisation**
  Nous avons du installer plusieurs librairies et mettre à jour la version de python. Pour cela nous avons executer différentes commandes dans le terminal. Certaine ibrairies étaient déja présente.
  Nous avons placé les balises en respectant la documentation technique. Les antennes doivent se situer à 15cm de la surface sur laquelle elles sont posés (possible grace a l'utilisation des support 3D). Elles doivent etre espacés l'une de l'autre de au moins 2 mètres.
  L'une des balise était défectueuse car le port micro-USB était cassé. Le temps de la réparer nous avons opté pour un système à 6 balises comme ci-dessous.
  
  ![alt tag](https://github.com/SAE3L/DroneSAE4/blob/main/Image/loco_ref_system_6_anchors.png)

  Une fois les balises physiquement placés nous les avons déclarés dans le logiciel. Nous avons donc mesuré les distances de nos balises par rapport a notre centre et les avons écrites dans le logiciel afin qu'il place les balises dans l'espace. Grace à cela il peut situer le drone  dans une visualisation 3D. 
![alt tag](https://github.com/SAE3L/DroneSAE4/blob/main/Image/Capture%20d%E2%80%99%C3%A9cran%20du%202024-06-13%2009-17-30.png)
