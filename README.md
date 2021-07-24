## Ubuntu ASUS PCIe Bus


Erreur: `PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e5(Receiver ID)`
Pour résoudre l'erreur, on va se rendre dans le menu grub qui ressemble à ça:
```
* Ubuntu
  Ubuntu (safe graphics)
  OEM install (for munfacturers)
  Boot from next volum
  UEFI Firmware Setting
```
et on va appuyer sur la touche `e` du clavier. Ensuite, un fichier va apparaître avec la ligne:

<code>linux      /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed maybe-ubiquity quiet <b>pci=noaer pcie_aspm=off</b> Splash</code>

On ajoute `pci=noaer pcie_aspm=off` à la ligne entre quiet et splash.

**À noter**: Le secure boot de l'ordinateur doit être désactivé.
[Liens vers la vidéos ASUS pour désactiver le secure boot](https://www.youtube.com/watch?v=tnOHi0w77bU)

À la fin de l'installation du système d'exploitation. J'ai eu un problème de black screen. Pour résoudre le problème, j'ai appuyer sur `esc` jusqu'à ce que le menu grub apparaisse. Ensuite, j'ai appuyé sur `e` pour affichier le fichier grub et j'ai ajouté `nomodeset pci=noaer` entre quiet et splash.

Avec le système ouvert, on va rendre les modifications permanentes.

Pour ce faire, j'ai fait la commande: `sudo nano /etc/default/grub`

Dans le fichier, la ligne devrait ressembler à ça:
<code>GRUB_CMDLINE_LINUX_DEFAULT="quiet <b>pci=noaer pcie_aspm=off nomodeset</b> splash"</code>

`Ctrl+W Enter Ctrl+X` 

Après avoir enregistré le fichier, on va entrer la commande: `sudo update-grub` et `reboot` pour vérifier le fonctionnement de la machine Ubuntu.
