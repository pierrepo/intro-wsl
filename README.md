# Windows Subsystem for Linux (WSL)

Ce document rassemble quelques ressources pour l'installation de Windows Subsystem for Linux (WSL).

WSL est un outil proposé par Microsoft pour installer Linux sur un système Windows.

Cette fonctionnalité n'est disponible que pour **Windows 10** 64 bits.


## Mise à jour 

Pour obtenir Linux sur un système Windows 10, vous devez tout d'abord vérifier que votre système est à jour.

## Installation de WSL

Exécutez l'instruction suivante dans un PowerShell en tant qu'administrateur (voir [copie d'écran](img/powershell_demo.jpg)) :
```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

Si ensuite, vous n'installez pas WSL2, redémarrez votre machine puis passez à l'étape *Installation d'une distribution Linux*.


## Installation de WSL 2

Depuis mai 2020, une nouvelle version de Windows Subsystem for Linux (WSL2) est disponible. Celle-ci est plus performante que WSL mais utilise une technologie différente.

**Attention** : WSL2 ne fonctionne pour l'instant pas dans une machine virtuelle de type VirtualBox. Dans ce cas, restez à WSL.

Pour installer WSL2, exécutez cette commande dans un PowerShell en tant qu'administrateur :
```
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

Toujours dans un PowerShell en tant qu'administrateur, exécutez ensuite l'instruction :
```
wsl --set-default-version 2
```
Si le message
```
WSL 2 requires an update to its kernel component. 
For information please visit https://aka.ms/wsl2kernel
```
apparait, suivez les nouvelles instructions :
- allez sur le site https://aka.ms/wsl2kernel, 
- cliquez sur *Téléchargez le dernier package de mise à jour du noyau Linux WSL2* pour lancer le téléchargement du fichier *wsl_update_x64.msi*,
- doublez-cliquez sur ce fichier pour l'exécuter,
- redémarrez votre machine.

Relancez ensuite l'instruction ci-dessous dans un PowerShell en tant qu'administrateur :
```
wsl --set-default-version 2
```

Si vous avez le message *Pour plus d'information sur les différences de clés avec WSL 2...*, tout va bien !

Une fois WSL2 installé, redémarrez votre machine.


## Installation d'une distribution Linux

À ce stade vous avez installé le sous-système Linux mais pas une distribution Linux à proprement dit.

Nous vous conseillons l'installation de la distribution Linux [Ubuntu 20.04](https://www.microsoft.com/fr-fr/p/ubuntu-2004-lts/9n6svws3rx71?activetab=pivot:overviewtab).

Pour cela, ouvrez le [Microsoft Store](https://aka.ms/wslstore) (voir [copie d'écran](img/microsoft_store_demo.jpg)), choisissez *Ubuntu 20.04 LTS* puis lancez le téléchargement et enfin l'installation.

L'installation va prendre quelques minutes. Vous choisirez ensuite un nouvel identifiant et un nouveau mot de passe. L'identifiant Linux doit être différent de votre identifiant Windows.

Remarque : vous n'avez pas besoin de mettre un mot de passe compliqué.

Un icône orange *Ubuntu 20.04 LTS* devrait apparaitre dans le menu (voir [copie d'écran](img/ubuntu_icon_demo.jpg)) et vous permettre de lancer un terminal Linux.


## Références et guides

Le document de référence pour l'installation de WSL et WSL2 (très détaillé) :

https://docs.microsoft.com/en-us/windows/wsl/install-win10


Guides et tutos pour l'installation de WSL :

- https://www.windowscentral.com/how-install-bash-shell-command-line-windows-10
- https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/
- https://www.howtogeek.com/265900/everything-you-can-do-with-windows-10s-new-bash-shell/


Guides et tutos pour l'installation de WSL2 :

- https://korben.info/installer-wsl2-windows-linux.html
- https://www.tech2tech.fr/installer-wsl-sous-syteme-linux-sur-windows-10/


## FAQ

### Depuis un terminal Linux, comment accéder à mes fichiers qui sont sous Windows ?

Le répertoire utilisateur de Windows est accessible depuis un terminal Linux en suivant ce chemin :

```
/mnt/c/Users/<windows-user>
```

où `<windows-user>` est le nom de l'utilisateur Windows.

