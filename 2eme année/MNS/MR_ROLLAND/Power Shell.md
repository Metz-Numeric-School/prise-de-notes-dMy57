



---

### SERVEUR 1 : 

Création VM Wserv sans interface graphique 

User (mdp user / Azerty01)

Option 3 : ajout d'un compte Admin

Aller vers le powershell (15)

```
net user administrateur * 
```

Mettre mdp admin :
``Pa$$word`` 

12 (fermer session)

Retour cmd puis connexion Admin

Vérifier IP de son serveur (8)

Ouvrir Power Shell (admin) machine hote :

```
Get-Service | Where-Object -Property Name -like "WinRM" | Start-Service
```

      + IP de ma machine

```
$vmIP="10.10.10.150"
```


Ajouter mon IP (10.10.10.150) aux trusted host

```
Set-Item wsman:\localhost\Client\TrustedHosts -value $vmIP -Force
```

Vérification de l'ajout du trusted host

```
Get-Item wsman:\localhost\Client\TrustedHosts
```

```
Enter-PSSession $vmIP -Credential .\administrateur 
```

Puis mettre mdp : ``(mdp : Pa$$word)``


Renommage Serv : 
```
$vmName="DC01"
```

```
Rename-Computer -NewName $vmName -Restart
```


Puis se reconnecter en SHH

---
Sélection de l'interface (1)
Definir l'adresse de la carte réseau (1)
S (IP statique)
Mettre masque + Gateway 

Ajouter l'ip statique au serveur : 10.10.10.152

---

Retour Powershell puis ajouter le trusted host de 10.10.10.152

```
$vmIP="10.10.10.152"
```

ajoute de vmIP aux trusted host
```
Set-Item wsman:\localhost\Client\TrustedHosts -value $vmIP -Force
```

Vérification de l'ajout : 

```
Get-Item wsman:\localhost\Client\TrustedHosts
```

Puis connexion : 

```
Enter-PSSession $vmIP -Credential .\administrateur
```

---
Depuis le PowerShell du serveur : 

SUPPRIMER ADRESSE : 

```
Get-NetIPAddress
``` 

permet de récupérer l interface index

Vérifier l'interface :  

```
Get-NetAdapter (numéro de l'index)
```

```
Get-NetAdapter -InterfaceIndex 6 | Remove-NetIPAddress -AddressFamily "IPv4"
```

Confirmation : oui 
Suppression de l'Apipa

```
Get-NetAdapter -InterfaceIndex 6 | New-NetIPAddress -AddressFamily "IPv4" -IPAddress "10.10.10.152" -PrefixLength 24 -DefaultGateway "10.10.10.254"
```

Vérification de ping 8.8.8.8 

```
Set-DnsClientServerAddress -InterfaceIndex 6 -ServerAddresses ("127.0.0.1", "8.8.8.8")
```

Ping google.fr (pour test)

---

On repasse en PowerShell puis on se connecte au serveur :

```
Enter-PSSession $vmIP -Credential .\administrateur
```


On ajoute le rôle ADDS : 

```
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools
```

```
$domainName="learn-it.local"
```

```
 $adminPassword=ConvertTo-SecureString "Azerty02" -AsPlainText -Force
```

```
Install-ADDSForest -DomainName $domainName -SafeModeAdministratorPassword $adminPassword
```

On vérifie si on est bien dans le domaine : 
![[Pasted image 20250325110853.png]]

Reconnexion en SSH (PowerShell)

```
Enter-PSSession $vmIP -Credential .learn-it.local\administrateur
```

On créé notre premier utilisateur : 

Création variable user name

```
$userName="toto"
```

Création variable mdp
```
$userPassword=ConvertTo-SecureString "MonMotDePasse1234" -AsPlainText -Force
```

Création 
```
New-ADUser -Name $userName -Accountpassword $userPassword -Enabled $true
```

Vérification de l'user : 
```
Get-ADUser -Filter * | Select-Object Name, SamAccountName
```


----

### Serveur 2 : 

User (mdp user / Azerty01)

Option 3 : ajout d'un compte Admin

Aller vers le powershell (15)

```
net user administrateur * 
```

Mettre mdp admin :
``Pa$$word`` 

12 (fermer session)

Retour cmd puis connexion Admin

Vérifier IP de son serveur (8)

Ouvrir Power Shell (admin) machine hote :

```
Get-Service | Where-Object -Property Name -like "WinRM" | Start-Service
```

   + IP de ma machine

```
$vmIP="10.10.10.151"
```


Ajouter mon IP (10.10.10.151) aux trusted host

```
Set-Item wsman:\localhost\Client\TrustedHosts -value $vmIP -Force
```

Vérification de l'ajout du trusted host

```
Get-Item wsman:\localhost\Client\TrustedHosts
```

```
Enter-PSSession $vmIP -Credential .\administrateur 
```

Puis mettre mdp : ``(mdp : Pa$$word)``


On configure le HostName :

```
$vmName="DC02"
```

```
Rename-Computer -NewName $vmName -Restart
```


Se reconnecter dans le PowerShell du PC : 

```
Enter-PSSession $ipVM -Credential .\administrator
```


Depuis le serveur : 

Sélection de l'interface (1)
Definir l'adresse de la carte réseau (1)
S (IP statique)
Mettre masque + Gateway 

Ajouter l'ip statique au serveur : 10.10.10.153 
CIDR : 255.255.255.0
GW : 10.10.10.254


Retour Powershell puis ajouter le trusted host de 10.10.10.153

```
$vmIP="10.10.10.153"
```

ajoute de vmIP aux trusted host
```
Set-Item wsman:\localhost\Client\TrustedHosts -value $vmIP -Force
```

Vérification de l'ajout : 

```
Get-Item wsman:\localhost\Client\TrustedHosts
```

Puis connexion : 

```
Enter-PSSession $vmIP -Credential .\administrateur
```


Depuis le PowerShell du Serveur : 

Ajout du Role ADDS sur le second server : 

```
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools
```

```
$domainName="learn-it.local"
```

```
$adminPassword=ConvertTo-SecureString "Azerty02" -AsPlainText -Force
```

```
Install-ADDSDomainController -InstallDns -Credential (Get-Credential $domainName\Administrateur) -DomainName $domainName -SafeModeAdministratorPassword $adminPassword -Force
```


Depuis le serveur 1 : 

```
$ifIndex = Get-NetAdapter | Select-Object -exp ifIndex
```

```
$dnsServer="10.10.10.152" # A EDITER SELON VOTRE CONFIG
```

```
Set-DnsClientServerAddress -InterfaceIndex $ifIndex -ServerAddresses ($dnsServer, 127.0.0.1)
```

-----

Résultats : 

Serv 1 
![[Pasted image 20250326103048.png]]

Serv 2 :
![[Pasted image 20250325144959.png]]

AD-toto
Azerty01

```
# Chemin vers le fichier CSV sur le bureau de la VM
$filePath = "C:\Users\ad-toto\Desktop\utilisateurs.csv"
```


```
# Importer le fichier CSV
$users = Import-CSV -Path $filePath
```

```
# Fonction pour générer un mot de passe fort
function Generate-Password {
    $length = 12
    $chars = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()'
    $password = -join ((Get-Random -Count $length -InputObject $chars) | ForEach-Object {$_})
    return $password
}
```


```
# Créer les utilisateurs et exporter les mots de passe
$passwords = @()
foreach ($user in $users) {
    $password = Generate-Password
    New-ADUser -Name $user.nom -GivenName $user.prenom -SamAccountName $user.login -UserPrincipalName "$($user.login)@learn-it.local" -Path "OU=Utilisateurs,DC=learn-it,DC=local" -AccountPassword (ConvertTo-SecureString $password -AsPlainText -Force) -Enabled $true -ChangePasswordAtLogon $true
    $passwords += [PSCustomObject]@{Username=$user.login;Password=$password}
}
```

```
# Exporter les noms d'utilisateur et les mots de passe dans un fichier CSV
$passwords | Export-CSV -Path "C:\Users\ad-toto\Desktop\passwords.csv" -NoTypeInformation
```

```
# Créer les groupes de sécurité et ajouter les utilisateurs
$groups = @("CADRE", "DIRIGEANT", "TECH")
foreach ($group in $groups) {
    if (-not (Get-ADGroup -Filter {Name -eq $group})) {
        New-ADGroup -Name $group -GroupScope Global -GroupCategory Security -Path "OU=Groupes,DC=learn-it,DC=local"
    }
}
```

```
foreach ($user in $users) {
    Add-ADGroupMember -Identity $user.groupe -Members $user.login
}
```


```
# Chemin vers le fichier CSV sur le bureau de la VM
$filePath = "C:\Users\ad-toto\Desktop\utilisateurs.csv"

# Importer le fichier CSV
$users = Import-CSV -Path $filePath

New-ADOrganizationalUnit -Name "TECH" -Path "DC=learn-it,DC=local"  
New-ADOrganizationalUnit -Name "DIRIGEANT" -Path "DC=learn-it,DC=local"  
New-ADOrganizationalUnit -Name "CADRE" -Path "DC=learn-it,DC=local"



# Vérifiez les valeurs importées
$users | ForEach-Object { Write-Host "Nom: $($_.nom), Prénom: $($_.prenom), Login: $($_.login), Groupe: $($_.groupe)" }

# Fonction pour générer un mot de passe fort
function Generate-Password {
    $length = 12
    $chars = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()'
    $password = -join ((Get-Random -Count $length -InputObject $chars) | ForEach-Object {$_})
    return $password
}

# Créer les utilisateurs et exporter les mots de passe
$passwords = @()
foreach ($user in $users) {
    if ($user.nom -and $user.prenom -and $user.login -and $user.groupe) {
        $password = Generate-Password
        try {
            $ouPath = "OU=$($user.groupe),DC=learn-it,DC=local"
            New-ADUser -Name $user.nom -GivenName $user.prenom -SamAccountName $user.login -UserPrincipalName "$($user.login)@learn-it.local" -Path $ouPath -AccountPassword (ConvertTo-SecureString $password -AsPlainText -Force) -Enabled $true -ChangePasswordAtLogon $true
            $passwords += [PSCustomObject]@{Username=$user.login;Password=$password}
        } catch {
            Write-Host "Erreur lors de la création de l'utilisateur $($user.login) : $_"
        }
    } else {
        Write-Host "L'utilisateur $($user.login) a des valeurs manquantes et n'a pas été créé."
    }
}

# Exporter les noms d'utilisateur et les mots de passe dans un fichier CSV
$passwords | Export-CSV -Path "C:\Users\ad-toto\Desktop\passwords.csv" -NoTypeInformation

# Créer les groupes de sécurité
$groups = @("CADRE", "DIRIGEANT", "TECH")
foreach ($group in $groups) {
    if (-not (Get-ADGroup -Filter {Name -eq $group})) {
        New-ADGroup -Name $group -GroupScope Global -GroupCategory Security -Path "DC=learn-it,DC=local"
    }
}

# Ajouter les utilisateurs aux groupes
foreach ($user in $users) {
    if ($user.groupe) {
        try {
            Add-ADGroupMember -Identity $user.groupe -Members $user.login
        } catch {
            Write-Host "Erreur lors de l'ajout de l'utilisateur $($user.login) au groupe $($user.groupe) : $_"
        }
    } else {
        Write-Host "L'utilisateur $($user.login) n'a pas de groupe spécifié."
    }
}
```