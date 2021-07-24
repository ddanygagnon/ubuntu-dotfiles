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
