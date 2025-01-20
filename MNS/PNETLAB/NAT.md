 
enable  
conf t  
int l'interface prive (ip nat inside) (int qui va vers le réseau) 
int interface public (in pnat outside) (int qui sors du réseau)
  
creer une acces list  :
  
acces-list` (nom de la liste) permit (adresse du réseau)  

**ex : acces-list 10 permit 192.168.0.0 0.0.0.255  (réseau inside)**
  
ip nat inside source list (nom de la list creer auparavant) int e0/1 (int qui sors) overload  
(permet de passer en pat )  

```
ip nat inside source 10 int E0/1 overload
```
  
apres faire une ip route entre les routeurs