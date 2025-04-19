# Étape 1 : Construire l'application
FROM node:18 AS build

# Définir le répertoire de travail
WORKDIR /app

# Copier les fichiers package.json et yarn.lock pour installer les dépendances
COPY package.json yarn.lock ./

# Installer les dépendances avec Yarn
RUN yarn install

# Copier le reste des fichiers du projet
COPY . .

# Étape 2 : Lancer le serveur de développement Vite
EXPOSE 5173

# Démarrer le serveur de développement Vite avec Yarn
CMD ["yarn", "dev"]