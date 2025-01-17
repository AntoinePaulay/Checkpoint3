
## Partie 1 : Gestion des utilisateurs
Q.2.1.1 Sur le serveur, créer un compte pour ton usage personnel.

![image](https://github.com/user-attachments/assets/ec6419d0-1bff-40d1-b42f-087e6f83ed27)


Q.2.1.2 Quelles préconisations proposes-tu concernant ce compte ?

Mots de passe fort, ajout au groupe sudo 

## Partie 2 : Configuration de SSH
Un serveur SSH est lancé sur le port par défaut.
Il est possible de s'y connecter avec n'importe quel compte, y compris le compte root.

Q.2.2.1 Désactiver complètement l'accès à distance de l'utilisateur root.

![image](https://github.com/user-attachments/assets/8f1d1567-1324-44ae-b567-db61a5fe8738)


Q.2.2.2 Autoriser l'accès à distance à ton compte personnel uniquement.

![image](https://github.com/user-attachments/assets/3573e9bd-eef7-44eb-8ca1-f895d32bed07)

Q.2.2.3 Mettre en place une authentification par clé valide et désactiver l'authentification par mot de passe

## Partie 3 : Analyse du stockage
Q.2.3.1 Quels sont les systèmes de fichiers actuellement montés ?


![image](https://github.com/user-attachments/assets/40e16585-e0e1-4f1c-a09c-3f90130d34fa)


Q.2.3.2 Quel type de système de stockage ils utilisent ?
raid 1 et lvm

Q.2.3.3 Ajouter un nouveau disque de 8,00 Gio au serveur et réparer le volume RAID


Q.2.3.4 Ajouter un nouveau volume logique LVM de 2 Gio qui servira à héberger des sauvegardes. Ce volume doit être monté automatiquement à chaque démarrage dans l'emplacement par défaut : /var/lib/bareos/storage.

Q.2.3.5 Combien d'espace disponible reste-t-il dans le groupe de volume ?

## Partie 4 : Sauvegardes
Le logiciel bareos est installé sur le serveur.
Les composants bareos-dir, bareos-sd et bareos-fd sont installés avec une configuration par défaut.

Q.2.4.1 Expliquer succinctement les rôles respectifs des 3 composants bareos installés sur la VM.

1. Bareos-dir: Bareos Director gère et supervise les operation de sauvegardes et leur restauration, controle les jobs et coordonne les actions entre les autre composants
2. Bareos_sd : Bareos Storage Daemon il est responsable du stokage et de la recuperation des données de sauvegarde, il gere l'ecriture et la lecture des données sur les support.
3. Bareos_fd : Bareos File Daemon il est le client de sauvegarde installé sur les machines a sauvegarder, il lis les fichier a sauvegarder et effectue leur transmission au Storage Daemon lors des sauvegarde.

Partie 5 : Filtrage et analyse réseau
Q.2.5.1 Quelles sont actuellement les règles appliquées sur Netfilter ?


![image](https://github.com/user-attachments/assets/0672a343-c18d-4667-83ca-dc823d16f062)


Q.2.5.2 Quels types de communications sont autorisées ?

Les communication autoriser sont   ct state established
                                   iifname
                                   tcp port 22 (ssh)
                                   icmp (Internet Control Message Protocol) en ipv4 
                                   icmp en ipv6

Q.2.5.3 Quels types sont interdit ?
rien 



Q.2.5.4 Sur nftables, ajouter les règles nécessaires pour autoriser bareos à communiquer avec les clients bareos potentiellement présents sur l'ensemble des machines du réseau local sur lequel se trouve le serveur.

![image](https://github.com/user-attachments/assets/7f8806cf-eb64-4fb5-ba96-3b866290e2d4)


Rappel : Bareos utilise les ports TCP 9101 à 9103 pour la communication entre ses différents composants.

## Partie 6 : Analyse de logs
Q.2.6.1 Lister les 10 derniers échecs de connexion ayant eu lieu sur le serveur en indiquant pour chacun :

![image](https://github.com/user-attachments/assets/0f490d08-d8ac-4c4c-a30d-940d25c2d156)


La date et l'heure de la tentative
L'adresse IP de la machine ayant fait la tentative
