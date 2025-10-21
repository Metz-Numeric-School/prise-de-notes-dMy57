sh
Trunk = selection des interfaces = switchport trunk encapsulation dot1q = sw mo tr

Ports "inactif" = selection des ports puis basculer dans VLAN "inactifs" puis les desactiver "shutdown" ou réactiver "noshut" 

sh vlan br = voir les vlan
sh interface trunk = voir les lien trunk
sh run = tout voirs

Router> enable  
Router# configure terminal  
 

**no shut (pnetlab) création SVI**
  
! Configurer gig0/0 port du routeur  
Router (config)#interface gi0/0/0  
Router (config)#no ip address  
  
  
! Sous-interface pour VLAN 10  
Router(config)# interface gi0/0/0.10  
Router(config-subif)# encapsulation dot1Q 10  
Router(config-subif)# ip address 192.168.10.254 255.255.255.0  
Router(config-subif)# exit  
  
! Répétez pour les autres VLANs  
Router(config)# interface gi0/0/0.20  
Router(config-subif)# encapsulation dot1Q 20  
Router(config-subif)# ip address 192.168.20.254 255.255.255.0  
Router(config-subif)# exit  
  
Router(config)# interface gi0/0/0.30  
Router(config-subif)# encapsulation dot1Q 30  
Router(config-subif)# ip address 192.168.30.254 255.255.255.0  
Router(config-subif)# exit  
  
Router(config)# interface gi0/0/0.40  
Router(config-subif)# encapsulation dot1Q 40  
Router(config-subif)# ip address 192.168.40.254 255.255.255.0  
Router(config-subif)# exit

