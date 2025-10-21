
La **NAT (Network Address Translation)** et la **PAT (Port Address Translation)** sont des techniques utilisées pour gérer les adresses IP dans un réseau.

### 1. **NAT (Network Address Translation)**

La NAT est un mécanisme qui permet de traduire une adresse IP privée en une adresse IP publique (et inversement). Elle est utilisée pour permettre aux appareils d'un réseau privé d'accéder à Internet via une seule adresse IP publique.

- **Types de NAT :**
    
    - **NAT statique** : Une adresse IP privée est toujours traduite en la même adresse IP publique.
        
    - **NAT dynamique** : Une adresse IP privée est traduite en une adresse IP publique choisie dynamiquement parmi un pool d'adresses disponibles.
        

### 2. **PAT (Port Address Translation) – Une forme spécifique de NAT**

La PAT est une variante de la NAT qui permet à plusieurs appareils d'un réseau privé de partager une seule adresse IP publique en différenciant les connexions à l'aide des numéros de port.

- Chaque appareil utilise un port source unique pour identifier ses connexions sortantes.
    
- Le routeur modifie les ports source des paquets sortants et garde une table de correspondance pour les paquets de réponse.
    

### 🔑 **Différences clés :**

| Critère               | NAT (Network Address Translation)                                     | PAT (Port Address Translation)                                                             |
| --------------------- | --------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| **Fonctionnement**    | Traduit une adresse IP privée en une adresse IP publique              | Traduit plusieurs adresses IP privées en une seule adresse publique en modifiant les ports |
| **Utilisation**       | Généralement pour une correspondance 1:1 ou depuis un pool d’adresses | Utilisé quand plusieurs appareils partagent la même adresse publique                       |
| **Gestion des ports** | Ne modifie pas forcément les ports                                    | Modifie les ports pour distinguer les connexions                                           |
| **Exemple**           | Un serveur interne accessible depuis une IP publique fixe             | Plusieurs utilisateurs accédant à Internet via une seule IP publique                       |
