# Projet OPSCI : Infrastructure complète avec objets connectés et architecture événementielle

## Developpeur :
- Deschamps Joseph 3802649
- Sacko Abdoul-Hakim 

## Présentation du projet
Ce projet offre une infrastructure complète permettant la création d'une plateforme de gestion de produits à grande échelle comprenant notamment une base de données, un système d'événements et des objets connectés.
Son déploiement se fait à partir d'images Dockers.

### Arborescence du projet

```
.
├── strapi/                     # app Strapi
|   └──Dockerfile               # Image personnalisée pour Strapi
├── frontend/                   # Frontend React
├── data/                       # Fichiers CSV (products, events, stocks)
├── docker-compose.yml          # Configuration des services Docker                  
├── scripts/                    # Scripts de gestion de l’infrastructure
│   ├── start.sh
│   └── stop.sh
└── README.md                   
```

## 1. Strapi
L'app Strapi vous permets de créer manuellement des produits, des évenements ou tout autre type d'entrée ainsi que de gérer les paramètres de votre plateforme.

### Collections créées :
- `product` avec : `name`, `description`, `stock_available`, `barcode`, `statut(enum)`
- `event` avec : `value`, `metadata (JSON)`

  
## 2. Kafka + Producers/Consumers
Kafka vous permets de gérer et de simuler un gransd nombre d'interactions (achat de stock, ajout de produit, évenement ...)

- **Topics** créés : `product`, `event`, `stock`, `error`
- **Fichiers CSV** placés dans le dossier `data/`
- **Volumes mappés** dans le docker-compose

  
## 3. Frontend React
Le frontend est issu de ce repo : [opsci-strapi-frontend](https://github.com/arthurescriou/opsci-strapi-frontend)

Il permet de visualiser depuis le port [localhost:5173](http://localhost:5173) les stocks de produits et les évenement en temps réel.


## 4. Accès rapides
- **L'app Starpi** : http://localhost:1337/admin
- **Le serveur React** : http://localhost:5173

## 5. Scripts de gestion

### `scripts/start.sh`
```bash
#!/bin/bash
echo "Lancement du programme"
docker compose down
docker compose up --build -d
```

### `scripts/stop.sh`
```bash
#!/bin/bash
echo "Arrêt du programme"
docker compose down
```

## 6. Utilisation

### Avant toute chose:
- Créer un fichier .env à la racine du projet
- Remplissez le comme suit:
```
DATABASE_CLIENT = postgres
DATABASE_HOST = 127.0.0.1
DATABASE_PORT= 5432
DATABASE_NAME= strapi
DATABASE_USERNAME= ${un username}
DATABASE_PASSWORD= ${un mot de passe} 
```

### Lancement du projet 
- exécuter /script/start.sh
- rendez vous sur [localhost:1337](http://localhost:1337) depuis un navigateur où vous trouverez l'app Strapi
  
### Configuration de Strapi
- Créer un profil admin
- Créer un `API TOKEN` dans les paramètres ( conserver le bien !!!)

### Dans le .env
- Rajoutez la ligne:
```
STRAPI_TOKEN= ${votre token}
```
### Dans le Frontend
- Modifier `frontend/src/conf.ts` avec le `TOKEN` issu de l'app Strapi (mode Admin)

### Félicitation, la configuration est fini ! Il ne vous reste qu'à relancer le projet:
- Restartez le programme à l'aide de la commande `./scripts/start.sh` 
- Vous pouvez maintenant vous rendre sur le serveur React pour observer l'activité des différents agents implementés.

## 7. Vidéo de démonstration
Une vidéo de démonstration du projet est disponible : 
