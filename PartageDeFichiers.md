<div align="center"><H1> Partage de fichiers </H1></div>

## Mise en pratique : Configuration d'un serveur de fichiers Windows

### Installation du rôle Serveur de fichiers

![1_AJOUT_ROLE.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Installation%20r%C3%B4le/1_AJOUT_ROLE.png)

![2_ROLE_FONCTIONNALITE.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Installation%20r%C3%B4le/2_ROLE_FONCTIONNALITE.png)

![3_SELECTION_SERVER.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Installation%20r%C3%B4le/3_SELECTION_SERVER.png)

![4_SERVICES_FICHIERS.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Installation%20r%C3%B4le/4_SERVICES_FICHIERS.png)

![5_SERVEUR_FICHIERS.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Installation%20r%C3%B4le/5_SERVEUR_FICHIERS.png)

### Création d'un partage



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
