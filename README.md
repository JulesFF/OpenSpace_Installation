<img src=https://img.shields.io/badge/Documentation-Installation-green]>
# Guide d'installation d'OpenSpace

## Prérequis

- Serveur avec Ubuntu Focal 20.04 

## Installation de [docker et docker-compose](https://docs.docker.com/engine/install/ubuntu/).

* Désinstaller les anciennes versions

```
sudo apt-get remove docker docker-engine docker.io containerd runc
```

* setup de l'installation
```
sudo apt-get update

sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

* ajouter la clé CPG officielle de docker:
```
sudo mkdir -p /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

* setup le repertoire
```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

* installer le docker engine
```
sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

* verifier que le docker engine fonctionne correctement
```
sudo docker run hello-world
```
## Installation de OpenSpace

* copier le fichier **openspace.tar.gz**  dans `~/home`

* dezipper le fichier  **openspace.tar.gz** 
```
tar xvzf openspace.tar.gz
```
* naviguer dans le dossier openspace
```
cd openspace
```
* s'assurer qu'il contient bien 2 fichiers
```
ls -la
```
on devrait voir les fichiers `.env` et `docker-compose.yml`

L'arborescence devrait etre la suivante:
```
home
└──openspace
   ├── .env
   └── docker-compose.yml
```

## Demarrage de l'application
On peut maintenant demarrer l'application
```
sudo docker-compose up
```
<sub>_NB: le premier démarrage peut prendre quelques minutes le temps de télécharger les packets nécéssaires_</sub>

Une fois que toutes les couches des images composantes l'application ont étés téléchargés, l'application se lancera toute seule

***Il faudra alors recupérer l'identifiant et le mot de passe administrateur dans les logs uniquement visibles lors du premier lancement!***

![example output](https://github.com/JulesFF/OpenSpace_Installation/output.png)

OpenSpace est desormais disponible sur le port 80 du serveur, accessible a travers un navigateur web en tapant l'addresse ip du serveur dans la barre de recherche!



