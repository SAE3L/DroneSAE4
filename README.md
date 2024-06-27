# Bienvenue sur le Projet SAÉ-4: Essaim de Drones dans l'Espace

<img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/iut_mulhouse.png' width = 300>
<img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/GEII.jpg' width = 300>

## Équipe : WEIGEL Léon - POULIN Loup - JAFFEUX Louis
## Enseignant Référents : M. HUEBER Eric - MOURLION Benjamin

### Merci à : BADER Alexandre - TRAN Kevin - KLEINKLAUS Romain - MAYABA Aklaa
> lien vers leurs GitHub : [DronesSAÉ4-2023](https://github.com/arduilex/SAE4_drone?tab=readme-ov-file)

# **SAÉ4 :**

# Sommaire :
1. Récupération du projet existant
2. Compréhension du projet existant
3. Définition d'un cahier des charges précis et d'un diagramme de GANTT
4. Communiquer avec un drone
5. Communiquer avec les balises de localisation


# **1 : Récupération du projet existant**
  La récupération du projet existant passe déjà pas la récupération du GitHub du projet de l'année dernière. La lecture de leurs traces écrites sur ce qu'ils avaient accompli. Ensuite un inventaire du matériel. On compte donc :
  8 balises de localisation, dont une défectueuse. 
  8 drones pilotables, dont un abimé.
  Des batteries portables pour alimenter les balises.
  Un PC sous Linux pour l'utilisation du client.
Si vous lisez ces mots dans le cadre de votre SAE sur ces drones : "Puisse le sort vous être favorable".

# **2 : Compréhension du projet existant**
  Le projet déjà existant consiste en un dossier de plusieurs scripts python, ces scripts ne sont pas annotés, on peut se fier uniquement au nom du script pour deviner leur utilité.
  Aussi le READ ME n'explique pas la procédure de mise en fonctionnement du projet, il faudra donc reprendre le projet de 0. On sait que l'ancien groupe a réussi à localiser les drones dans l'espace, ce qui est la finalité du projet.
  <img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/matos.jpg' width = 500>

  (Matériel avec ajouts personnel : protections drones et supports balises)

### **2.1 : Étude de fonctionnement des drones**
  On a pu découvrir la signalétique des drones, en effets, les drones communiquent des informations à l’utilisateur via ces différentes LEDs : 

  <img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/DirectionDroneOrientation.png' width = 600>
  
  2X Led rouge = Erreur capteur d’inclinaison
  
  2X Led rouge rapide = Erreur Extension
  
  Bleu clignotant = Erreur batterie / batterie vide
  
  Led 4 verte = opérationnel
  
  Led 4 jaune = téléversemment
  
  Led 1 verte = en attente

  De plus, n'ayant jamais piloté de drones, on a pu grâce au site bitcraze, sur la catégorie introductions et mise en marche pas à pas, découvrir ce qu'est que le : **Yaw, Roll, Pitch & Thrust**, respectivement : Lacet, Roulis Tangage et Poussée.
  On peut bien le voir sur l'image suivante : 

  <img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/Axes.png' width = 600>

### **2.2 : Étude de fonctionnement des balises**
  On a dû comprendre comment fonctionnaient les balises (aussi appelées nodes). Pour ce faire, nous avons étudié les différents modes TWR, TDOAT2 et TDOAT3. Dans tous les cas, il s'agit de comprendre la distance entre la balise et le drone en calculant le temps que prend une information radio à être envoyée de l'antenne au drone et la réception de cette information.
  
Vous pouvez voir plus d'informations sur ce lien : [lien du wiki sur les balises](https://wiki.bitcraze.io/projects:lps:node)

**TWR :** c'est un mode de connexion à 6 antennes, deux triangles inversés dans l'espace. Idéal pour le commencement pour la configuration du client et des balises.

**TDOAT2 & TDOAT3 :** Plus stable, peut être utilisé à 6 ou 8 balises, peut gagner en précision pour des corrections de positions

# **3 : Définition d'un cahier des charges précis et d'un diagramme de GANTT**
  On a dû essayer de hiérarchiser les différentes tâches à effectuer. N'ayant pas de consigne précise, on a pour objectif d'accomplir ces tâches les unes après les autres le plus loin possible.
  
![alt tag](https://github.com/SAE3L/DroneSAE4/blob/main/Organisation/Gantt.PNG)

# **4 : Communiquer avec un drone**
  On a réinstallé les différentes librairies proposées par crazyflie. Grace a elle on a réussi à exécuter du code python, qui grâce aux librairies peut se connecter aux drones. Après quelques essais, on arrive à récupérer l'orientation des drones et leurs rotations sur les 3 axes. On a une partie code qui se connecte avec l'antenne au drone, et une partie qui récupère ces informations en temps réel. Le script python ne peut pas s'exécuter en même temps que l'application client. La communication est limitée, il faut donc mettre l'antenne proche de la zone d'action des drones. Le code peut appeler différentes bibliothèques pour les faire décoller ou atterrir, si on stop le script les moteurs du drone s'arrêtent immédiatement. Les drones ont tendance à se mettre en défaut, reconnaissable grâce à une Led rouge qui clignote sur l'une des branches du drone. À ce moment-là, le drone est encore allumé, mais ne communique plus avec le PC.

le wiki : https://wiki.bitcraze.io/

![alt tag](https://github.com/arduilex/SAE4_drone/blob/main/images/overview_clientsoftware.jpg?raw=true)

# **5 : Communiquer avec les balises de localisation**
  Nous avons dû installer plusieurs librairies et mettre à jour la version de python. Pour cela, nous avons exécuté différentes commandes dans le terminal. Certaines librairies étaient déjà présentes.
  Nous avons placé les balises en respectant la documentation technique. Les antennes doivent se situer à 15 cm de la surface sur laquelle elles sont posées (possible grâce à l'utilisation des supports 3D). Elles doivent être espacées l'une de l'autre d’au moins 2 mètres.
  L'une des balises était défectueuse car le port micro-USB était cassé. Le temps de la réparer nous avons opté pour un système à 6 balises comme ci-dessous. Pour tester la bonne connexion des balises on peut utiliser l'application client. La connexion nécessite qu'il y ait un drone fonctionnel allumé, et que l'entièreté des balises (6 ou 8) soit allumé et fonctionnelle, sinon aucune balise n'apparait sur l'application client.

  <img src='https://github.com/SAE3L/DroneSAE4/blob/main/Image/loco_ref_system_6_anchors.png' width = 600>
  <img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/Principe_Com_Drone_Ancre.png' width = 600>
  
  Ci-dessous un schéma d'une balise
  
  <img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/schema_node.png' width = 600>

  Lors de l'essai de connexion à 8 balises, nous nous sommes rendu compte que la balise 5 (dont il manquait le port micro-USB) était configuré en TWR tandis que nous avions connectés les autres en TDoA2. Il n'était donc pas possible d'utiliser les système à 8 balises.  La seule manière d'envoyer les informations à la balise 5 que nous alimentions avec un simple bornier serait de brancher le port annoté 8 sur le schéma.
 
  Ci-dessous on remarque les différentes connexions.
  
  <img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/connexion1.png' width = 400>
  <img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/connexion2.png' width = 400>
  
  Une fois les balises physiquement placées, nous les avons déclarés dans le logiciel. Nous avons donc mesuré les distances de nos balises par rapport à notre centre et les avons écrites dans le logiciel afin qu'il place les balises dans l'espace. Grâce à cela il peut situer le drone dans une visualisation 3D. Ici, nous utilisons le mode TDoA2 qui permet d'utiliser 6 balises ou 8 balises (il est préférable d'utiliser ce mode car les balises sont déjà configurées dans celui-ci). 
![alt tag](https://github.com/SAE3L/DroneSAE4/blob/main/Image/Capture%20d%E2%80%99%C3%A9cran%20du%202024-06-13%2009-17-30.png)

Le [script Python](https://github.com/SAE3L/DroneSAE4/blob/main/code%20position%20drone) configure et contrôle un drone Crazyflie à l'aide d'un système de positionnement Loco Positioning System (LPS) composé de six ancres, créant un espace de référence pour le positionnement précis du drone. Après avoir importé les bibliothèques nécessaires, le script initialise les positions des ancres et les configure via la fonction write positions_to_anchors. Il établit ensuite une connexion avec le drone en utilisant SyncCrazyflie et MotionCommander. Le programme initialise également un logger de position (PoseLogger) pour enregistrer les positions du drone en temps réel. Ensuite, il définit une cible de position et, à chaque itération d'une boucle de 100 cycles, il imprime la position actuelle du drone et envoie un point de consigne de position pour maintenir une hauteur de 2 mètres. Enfin, après ces itérations, le drone est commandé à atterrir. Le programme assure une communication efficace avec le drone et un contrôle précis de sa position grâce aux ancres LPS, permettant ainsi de tester et de démontrer les capacités de navigation autonome du drone dans un espace défini.

**Problèmes de connection**
Lors de la connexion depuis le client, les balises ne sont parfois pas détectées, elles sont encadrées en rouge. La solution que nous avons trouvée à cela est de flashé les balises une à une. Il faut pour cela utiliser l'application lps configuration tool. On peut l'ouvrir dans le terminal en utilisant la commande : 

```python3 -m lpstools```

Il faut ensuite aller dans la section "configure node" rentrer le numéro de la balise (pour plus de simplicité utiliser celui collé sur la balise) et définir en quel mode il sera utilisé.

<img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/lps_tool.png' width = 600>

# **6 : Protéger physiquement les drones**
  Les différents essais de vols ont soulevé un problème. La fragilité excessive des drones et le besoin de trouver une solution. Pour cela, nous avons fait des recherches sur des "armures de drones" c’est-à-dire des protections plastiques qui pourraient protéger le drone et ses hélices des contacts. On a trouvé des modèles 3D sur internet pour protéger les drones, après plusieurs essais, on a récupéré un modèle qui fonctionne qu'il a fallu adapter aux drones. Nous avons imprimé les supports à l'IUT lab.

Le premier support était facile à monter, mais moins pratique (les hélices peuvent toucher la structure).

&nbsp;<img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/protectiondrone2.jpg' width = 300>

[lien du support](https://www.myminifactory.com/object/3d-print-crazyflie-bumper-cage-with-battery-holder-54937)

Le deuxième est plus long à monter, mais est beaucoup plus fiable. Il est aussi plus rapide à imprimer. 

&nbsp;<img src='https://raw.githubusercontent.com/SAE3L/DroneSAE4/main/Image/protectiondrone1.jpg' width = 300>

[lien du support](https://www.printables.com/en/model/76336-crazyflie-21-cage-prop-guard)



# **7 : Situation actuelle**
  Contrairement à ce que l'on avait pu croire, le groupe précédant n'avait pas effectué de vol grâce à la localisation par balise. Grâce à un code proposé par le constructeur, nous avons réussi à combiner la partie commande et localisation du drone. Ce qui a permis de faire un programme qui permet d'entrer une coordonnée à laquelle le drone doit se rendre. On lui avait demandé d'aller à 0 ; 0 ; 20, soit 20 cm au-dessus de l'origine. Le script s'est montré concluant, car le drone décolle, se place à 20 cm en hauteur, puis arrête de monter et reste à la consigne. Malheureusement le drone a dévié et est parti en diagonale dans le plafond dans le coin de la salle. On remarque donc rapidement que sa position x, y et z s'incrémente constamment dans le code comme dans l’application. Le drone croit qu'il se déplace, corrige le déplacement, et donc se déplace réellement. Cela peut être dû à deux facteurs, soit le drone est en erreur, soit les balises se déconnectent au lancement du programme.
