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

Ouvre l'Explorateur de fichiers

![VirtualBoxVM_SBSAsK58dh.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Via%20l'interface%20graphique%20(gui)/VirtualBoxVM_SBSAsK58dh.png)

Clique droit sur "Ce PC" > "Connecter un lecteur réseau"

![VirtualBoxVM_uLarZQXjWT.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Via%20l'interface%20graphique%20(gui)/VirtualBoxVM_uLarZQXjWT.png)

Choisis une lettre de lecteur
Entre le chemin du partage (ex: \\nom_serveur\Ressourcesv2)
Coche "Se reconnecter à l'ouverture de session" si désiré

![VirtualBoxVM_b3Q4tcTaYd.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Via%20l'interface%20graphique%20(gui)/VirtualBoxVM_b3Q4tcTaYd.png)

Clique sur "Terminer"

![VirtualBoxVM_DZJf1vgout.png](https://github.com/Skchaper/PartageFichiers/blob/main/Screens/Via%20l'interface%20graphique%20(gui)/VirtualBoxVM_DZJf1vgout.png)

### Via PowerShell

L'utilisation de PowerShell permet d'automatiser la configuration des lecteurs réseau, ce qui est particulièrement utile dans les grands environnements.

Pour mapper un lecteur réseau :

**New-PSDrive -Name "Z" -PSProvider FileSystem -Root "\\nom_serveur\Ressourcesv2" -Persist**

Pour voir les lecteurs mappés :

**Get-PSDrive -PSProvider FileSystem**

<div align="center"><H1> Challenge </H1></div>

Sur un Windows Server 2022 avec le rôle ADDS déployé sur une VM :

**Installe le rôle Serveur de fichiers**

Voir la première partie de ce document.

**Crée un dossier "Documents_Entreprise" à la racine du disque C:**



**Configure un partage nommé "Docs" pour ce dossier**



**Crée trois sous-dossiers : "RH", "Comptabilité" et "Direction"**



**Configure les permissions NTFS et de partage pour que :**



**Le groupe "RH" ait un accès en lecture/écriture au dossier "RH"**



**Le groupe "Comptabilité" ait un accès en lecture/écriture au dossier "Comptabilité"**



**Le groupe "Direction" ait un accès en lecture/écriture à tous les dossiers**



**Tous les utilisateurs du domaine aient un accès en lecture seule au dossier "Documents_Entreprise"**



**Utilise PowerShell pour lister tous les partages sur le serveur**



**Sur un poste client Windows 10, configure un lecteur réseau pointant vers ce partage via PowerShell**



**Teste l'accès depuis le poste client avec différents comptes utilisateurs**

