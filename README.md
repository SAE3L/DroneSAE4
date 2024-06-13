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
  1. Communiquer avec un drone
  3. Communiquer avec les balises
  4. Initialiser la zone de vol
  5. Repérer ls drones dans l'espace
# **4 : Communiquer avec un drone**
  On a réinstaller les differentes librairies proposé par crazy fly. Grace a elle on a réussi a executer du code python, qui grace au librairie peut se connecter au drones.
  Apres quelques essais ont arrive a récuperer l'orientation des drones, leurs rotations sur les 3 axes. On a donc une partie code qui se connecte avec l'antenne au drone, et une partie qui récupère ces inforlations en temps réelle.
  Le script python ne peut pas s'executer en même temps que l'application client.


# **5 : Communiquer avec les balises de localisation**
  les balises de comunications ont nécessité d'installer plusieurs librairies, directement dans la console de Linux ce qui peut vite être compliqué pour des utilisateurs window.


# **6 : Initialiser la zone de vol**
