

#### **Type 2 (logiciel sans O.S)**
- VM Ware Workstation
- Virtual Box
- Hyper V (W10 et et 11 Pro)

#### **Type 1 (O.S)**
- Proxmox
- Hyper V (Windows Serveur)
- VM Ware EXSXI

= HYPERVISEUR


### ETAPE 1 : 

- TOPOLOGIE PHYSIQUE (emplacement + cables)
- TOPOLOGIE LOGIQUE (interfaces + adresses IP)
- Préparation de l'installation
	- clé USB bootable = procédure
	- pré-requis (mémoire, disque, etc ...)


### ETAPE 2 : 

- Installation et paramétrage 

### ETAPE 3 : 

- Création de VM (x = 1/chacun) s

---

1 : image1: Installation graphique*
2 : Image2: Configuration 
3 : Image3: TimeZone, Pays
4: Image4: Password: ``Pa$$word``
5: Image5: Server IP: 10.10.10.100
6: Image 6: Recap
7: Image7: Installation
8 : reboot 
9 : F11



changer l'adresse ip de l'interface avec : 
```
sudo ip addr add 192.168.1.100/24 dev eno2
```

et mettre l'int en up 

```
sudo ip link set eno2 up
```

installer : 
```
virtio-win-01
```

