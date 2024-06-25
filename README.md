# Bienvenue sur le Projet SAÉ-4: Essaim de Drones dans l'Espace

<img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/iut_mulhouse.png' width = 600>
<img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/GEII.jpg' width = 300>

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
  Un PC sous linux pour l'utilisation du client.
Si vous lisez ces mots dans le cadre de votre SAE sur ces drones : "Puisse le sort vous être favorable".

# **2 : Compréhension du projet existant**
  Le projet déja existant consiste en un dossier de plusieurs script python, ces scripts ne sont pas annoter, on peut se fier uniquement au nom du script pour deviner leur utilité.
  Aussi le READ ME n'explique pas la procédure de mise en fonctionnement du projet, il faudra donc reprendre le projet de 0. On sait que l'ancien groupe a réussi a localiser les drones dans l'espace ce qui est la finalité du projet.
  ![alt tag](https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/matos.jpg)
  (matériel avec ajouts personnel : protections drones et supports balises)

### **2.1 : Étude de fonctionnement des drones**
  blablabla

### **2.2 : Étude de fonctionnement des balises**
  On a du comprendre comment fonctionnais les balises (aussi appellées nodes). Pour ce faire nous avons étudié les différents modes TWR, TDOAT2 et TDOAT3. Dans tout les cas il s'agit de comprendre la distance entre la balise et le drone en calculant le temps que prend une information radio à être envoyée de l'antenne au drone et la reception de cette information.
Vous pouvez voir plus d'informations sur ce liens : [lien du wiki sur les balises](https://wiki.bitcraze.io/projects:lps:node)

**TWR :** c'est un mode de connection à 6 antennes, deux triangles inversés dans l'espace. Idéal pour le commencement pour la configuration du client et des balises.

**TDOAT2 & TDOAT3 :** Plus stable, peut être utilisés à 6 ou 8 balises, peut gagner en precision pour des correction de positions

# **3 : Définition d'un cahier des charges précis et d'un diagramme de GANTT**
  On a du essayer de hierarchisé les differentes tâches a effectuer. N'ayant pas de consigne précise on a pour objectif d'accomplir ces tâches les une après les autres le plus loin possible.
  
![alt tag](https://github.com/SAE3L/DroneSAE4/blob/main/Organisation/Gantt.PNG)

# **4 : Communiquer avec un drone**
  On a réinstaller les differentes librairies proposé par crazyflie. Grace a elle on a réussi a executer du code python, qui grace au librairie peut se connecter aux drones. Apres quelques essais on arrive a récuperer l'orientation des drones et leurs rotations sur les 3 axes. On a une partie code qui se connecte avec l'antenne au drone, et une partie qui récupère ces informations en temps réel. Le script python ne peut pas s'executer en même temps que l'application client. La comunication est limitée il faut donc mettre l'antenne proche de la zone d'action des drones. Le code peut appeller differentes bibliothèques pour les faire décoller ou atterir, si on stop le script les moteurs du drone s'arrettent imédiatement. Les drones ont tendancent a se mettre en défaut, reconnaissable grâce a une led rouge qui clignote sur l'une des branche du drone. A ce moment la, le drone est encore allumé, mais ne communique plus avec le PC.

le wiki : https://wiki.bitcraze.io/

![alt tag](https://github.com/arduilex/SAE4_drone/blob/main/images/overview_clientsoftware.jpg?raw=true)

# **5 : Communiquer avec les balises de localisation**
  Nous avons du installer plusieurs librairies et mettre à jour la version de python. Pour cela nous avons executer différentes commandes dans le terminal. Certaine ibrairies étaient déja présente.
  Nous avons placé les balises en respectant la documentation technique. Les antennes doivent se situer à 15cm de la surface sur laquelle elles sont posés (possible grace a l'utilisation des support 3D). Elles doivent etre espacés l'une de l'autre de au moins 2 mètres.
  L'une des balise était défectueuse car le port micro-USB était cassé. Le temps de la réparer nous avons opté pour un système à 6 balises comme ci-dessous. Pour tester la bonne conection des balises on peut utiliser l'application client. La connexion nécessite qu'il y est un drone fonctionnel allumé, et que l'entierté des balises(6 ou 8) soit allumé et fonctionnele, sinon aucune balise n'apparait sur l'application client.

  <img src='https://github.com/SAE3L/DroneSAE4/blob/main/Image/loco_ref_system_6_anchors.png' width = 600>

  Une fois les balises physiquement placés nous les avons déclarés dans le logiciel. Nous avons donc mesuré les distances de nos balises par rapport a notre centre et les avons écrites dans le logiciel afin qu'il place les balises dans l'espace. Grace à cela il peut situer le drone  dans une visualisation 3D. Ici nous utilisons le mode TDoA2 qui permet d'utiliser 6 balises ou 8 balises (il est préférable d'utiliser ce mode car les balises sont déjà configuré dans celui-ci). 
![alt tag](https://github.com/SAE3L/DroneSAE4/blob/main/Image/Capture%20d%E2%80%99%C3%A9cran%20du%202024-06-13%2009-17-30.png)

Le [script Python](https://github.com/SAE3L/DroneSAE4/blob/main/code%20position%20drone) configure et contrôle un drone Crazyflie à l'aide d'un système de positionnement Loco Positioning System (LPS) composé de six ancres, créant un espace de référence pour le positionnement précis du drone. Après avoir importé les bibliothèques nécessaires, le script initialise les positions des ancres et les configure via la fonction write_positions_to_anchors. Il établit ensuite une connexion avec le drone en utilisant SyncCrazyflie et MotionCommander. Le programme initialise également un logger de position (PoseLogger) pour enregistrer les positions du drone en temps réel. Ensuite, il définit une cible de position et, à chaque itération d'une boucle de 100 cycles, il imprime la position actuelle du drone et envoie un point de consigne de position pour maintenir une hauteur de 2 mètres. Enfin, après ces itérations, le drone est commandé à atterrir. Le programme assure une communication efficace avec le drone et un contrôle précis de sa position grâce aux ancres LPS, permettant ainsi de tester et de démontrer les capacités de navigation autonome du drone dans un espace défini.

**Problèmes de connection**
Lors de la connection depuis le client, les balises ne sont parfois pas détectés, elles sont encadrés en rouge. La solutions que nous avons trouvé à cela est de flasché les balises une à une. Il faut pour cela utiliser l'application lps configuration tool. On peut l'ouvrir dans le terminal en utilisant la commande : 

```python3 -m lpstools```

Il faut ensuite aller dans la section "configure node" rentrer le numéro de la balise (pour plus de simplicité utiliser celui collé sur la balise) et définir en quel mode il sera utilisé.

<img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/lps_tool.png' width = 600>

# **6 : Proteger physiquement les drones**
  Les différents essais de vols ont soulever un problème. La fragilité excessive des drones, et le besoin de trouver une solution. Pour cela nous avons fait des recherches sur des "armures de drones" c'est a dire des protection platisque qui pourrai proteger le drone et ses hélices des contacts. On a trouvé des models 3D sur internet pour proteger les drones, après plusieurs éssais, on a récupere un modèle qui fonctionne qu'il a fallu adapter aux drones. Nous avons imprimer les supports à l'IUT lab.

Le premier support était facile à monter mais moins pratique (les hélices peuvent toucher la structure)

&nbsp;<img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/protectiondrone2.jpg' width = 300>

[lien du support](https://www.myminifactory.com/object/3d-print-crazyflie-bumper-cage-with-battery-holder-54937)

Le deuxième est plus long à monter mais est beaucoup plus fiable. Il est aussi plus rapide à imprimer. 

&nbsp;<img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/protectiondrone1.jpg' width = 300>

[lien du support](https://www.printables.com/en/model/76336-crazyflie-21-cage-prop-guard)



# **7 : Situation actuelle**
  Contrairement a ce que l'on avais pu croire, le groupe précédant n'avais pas éfféctuer de vol grace a la localisation par balise. Grace a un code proposé par le constructeur, on a réussi a combiner la partie commande du drones et localisation du drone. Ce qui a permit de faire un programme qui permet d'entrée une coordonnées a laquelle le drone doit se rendre. On lui avait demandé d'aller a 0; 0; 20. Soit 20cm au dessus de l'origine. Le script s'est montré concluant car le drone décolle, se place a 20cm en hauteur. Puis arrète de monter et reste a la consigne. Le problème rencontré est que les balises en X et Y bug, les coordonnées X et Y s'incrémente en continue dans le positif. Donc le drone croit qu'il séplace, corrige le déplacement, et donc se déplace réellement. Ce qui fait que le drone vol vers un coin de la zone et ne s'arrete jamais alors même qu'il reste a 20cm de hauteur sans dévier en hauteur.
