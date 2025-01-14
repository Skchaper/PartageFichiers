<div align="center"><H1> Partage de fichiers </H1></div>

## Mise en pratique : Configuration d'un serveur de fichiers Windows

### Installation du rôle Serveur de fichiers

Clique sur "Gérer" > "Ajouter des rôles et fonctionnalités"

![1_AJOUT_ROLE.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Installation%20r%C3%B4le/1_AJOUT_ROLE.png)

Choisis "Installation basée sur un rôle ou une fonctionnalité"

![2_ROLE_FONCTIONNALITE.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Installation%20r%C3%B4le/2_ROLE_FONCTIONNALITE.png)

Sélectionne ton serveur

![3_SELECTION_SERVER.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Installation%20r%C3%B4le/3_SELECTION_SERVER.png)

Dans la liste des rôles, coche "Services de fichiers et de stockage" > "Serveur de fichiers"

![4_SERVICES_FICHIERS.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Installation%20r%C3%B4le/4_SERVICES_FICHIERS.png)

Suis l'assistant pour terminer l'installation

![5_SERVEUR_FICHIERS.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Installation%20r%C3%B4le/5_SERVEUR_FICHIERS.png)

### Création d'un partage

Dans le Gestionnaire de serveur, va dans "Services de fichiers et de stockage" > "Partages"

![1_SERVICES_FICHIERS.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Cr%C3%A9ation%20partage/1_SERVICES_FICHIERS.png)

Clique droit > "Nouveau partage"

![2_PARTAGE_NOUVEAU.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Cr%C3%A9ation%20partage/2_PARTAGE_NOUVEAU.png)

Choisis "Partage SMB - Rapide"

![3_SMB_RAPIDE.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Cr%C3%A9ation%20partage/3_SMB_RAPIDE.png)

Sélectionne l'emplacement du dossier à partager

![4_EMPLACEMENT.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Cr%C3%A9ation%20partage/4_EMPLACEMENT.png)

Nomme ton partage

![5_NOM_PARTAGE.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Cr%C3%A9ation%20partage/5_NOM_PARTAGE.png)

Configure les permissions NTFS et de partage selon tes besoins

![6_CONFIRMATION.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Cr%C3%A9ation%20partage/6_CONFIRMATION.png)

Termine l'assistant

![7_FERMER.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Cr%C3%A9ation%20partage/7_FERMER.png)

### Configuration avancée avec PowerShell

L'utilisation de PowerShell permet une configuration plus rapide et automatisable du serveur de fichiers.

Pour créer un partage via PowerShell :

**New-SmbShare -Name "Ressourcesv2" -Path "C:\Partages\Ressourcesv2" -FullAccess "Tout le monde"**

Pour voir les partages existants :

**Get-SmbShare**

## Configuration des lecteurs réseau sur les clients


### Via l'interface graphique (GUI)



### Via PowerShell

L'utilisation de PowerShell permet d'automatiser la configuration des lecteurs réseau, ce qui est particulièrement utile dans les grands environnements.

Pour mapper un lecteur réseau :

**New-PSDrive -Name "Z" -PSProvider FileSystem -Root "\\nom_serveur\Ressourcesv2" -Persist**

Pour voir les lecteurs mappés :

**Get-PSDrive -PSProvider FileSystem**
