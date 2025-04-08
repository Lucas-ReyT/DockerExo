# Déploiement MERN sans docker-compose

Reprenez l'application que vous avez déployée lors de votre cours MERN.  
Déployez là en local, avec docker, sans passer par docker-compose.  
Conteneurisez le front et l'API (création de dockerfiles et test des images buildées)  
Créez un volume pour la DB et déployez un conteneur mongodb  
Adaptez votre code afin qu'il utilise les noms de vos conteneurs dans vos URL.  
Lancez les trois conteneurs en réseau  

---

## 1. Création du réseau

```bash
docker network create network-projet-mern

2. Mongo

docker volume create mongo-data

docker run -d \
  --name db-container \
  --network network-projet-mern \
  -v mongo-data:/data/db \
  -p 27017:27017 \
  mongo

3. Backend

docker build -t express-project -f backend/Dockerfile .

docker run -d \
  -p 5201:3000 \
  --name back \
  --network network-projet-mern \
  express-project

4. Frontend

docker build -t react-project -f frontend/Dockerfile .

docker run -d \
  -p 5173:80 \
  --name front \
  --network network-projet-mern \
  react-project
