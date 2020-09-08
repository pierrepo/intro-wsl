# Windows Subsystem for Linux (WSL)

Ce document rassemble quelques ressources pour l'installation de Windows Subsystem for Linux (WSL).

WSL est un outil proposé par Microsoft pour installer Linux sur un système Windows.

Cette fonctionnalité n'est disponible que pour **Windows 10**.


## Installation de WSL

Pour obtenir Linux sur un système Windows 10, vous devez tout d'abord vérifier que votre système est à jour.

Exécutez ensuite l'instruction suivante dans un PowerShell en tant qu'administrateur :
```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

Si vous n'installez pas WSL2, redémarrez votre machine.

## Installation de WSL 2

Depuis mai 2020, une nouvelle version de Windows Subsystem for Linux (WSL2) est disponible. Celle-ci est plus performante que WSL mais utilise une technologie différente.

Attention, WSL2 ne fonctionne pas dans une machine virtuelle de type VirtualBox. Restez à WSL.

Pour installer WSL2, exécutez cette commande dans un PowerShell en tant qu'administrateur :
```
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```
puis l'instruction :
```
wsl --set-default-version 2
```
Si le message
```
WSL 2 requires an update to its kernel component. For information please visit https://aka.ms/wsl2kernel
```
apparait, suivez les nouvelles instructions indiquées.

Une fois WSL2 installé, redémarrez votre machine.

## Installation d'une distribution Linux

Nous vous conseillons l'installation de la distribution Linux [Ubuntu 20.04](https://docs.microsoft.com/en-us/windows/wsl/install-win10).

Pour cela, ouvrez le [Store Microsoft](https://aka.ms/wslstore), choisissez *Ubuntu 20.04 LTS* puis installez-la.

Lancez votre distribution Linux (un nouvel icône devrait apparaire dans le menu). Au premier lancement, vous devrez choisir un nouvel identifiant et un nouveau mot de passe. L'identifiant Linux doit être différent de votre identifiant Windows.

Remarque : vous n'avez pas besoin de mettre un mot de passe compliqué.


## Références et guides

Le document de référence pour l'installation de WSL et WSL2 :

https://docs.microsoft.com/en-us/windows/wsl/install-win10


Guides et tutos pour l'installation de WSL :

- https://www.windowscentral.com/how-install-bash-shell-command-line-windows-10
- https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/
- https://www.howtogeek.com/265900/everything-you-can-do-with-windows-10s-new-bash-shell/


Guides et tutos pour l'installation de WSL2 :




## Serveur X

Nous vous conseillons également d'installer un serveur X qui vous permettra de lancer des logiciels graphiques sous Linux (par exemple l'éditeur de texte gedit).

Pour cela, sous Windows :

- installez le logiciel [VcXsrv](https://sourceforge.net/projects/vcxsrv/),
- lancez-le en cliquant sur l'icône dans la barre de tâches et activez le fait qu'il tourne en tâche de fond.

Sous Linux, tapez la commande 
```
export DISPLAY=:0
```

Vous pouvez ensuite lancer un logiciel graphique. Par exemple :
```
gedit
```

Nous vous conseillons d'ajouter la ligne 
```
export DISPLAY=:0
```
à la fin du fichier de configuration `~/.bashrc`. Cette instruction sera ainsi prise en compte à chaque fois que vous lancerez un terminal sous Linux.


## FAQ