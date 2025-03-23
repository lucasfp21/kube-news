# Criacao da imagem da app:
    docker build -t lufertony/kube-news:v2 .    
        Rodou de dentro do src onde esta o Dockerfile

# Adicionando TAG
    docker tag lufertony/kube-news:v2 lufertony/kube-news:latest

# Fazendo push para o docker hub 
    docker push lufertony/kube-news:latest
    docker push lufertony/kube-news:v1

# Criando network
    docker network create kubenews_net

# Criando volume
    docker volume create kubenews_vol  

# Subindo container do Postgres
    docker container run -d -p 5432:5432 --name kubenews_db -e POSTGRES_PASSWORD=Pg123 -e POSTGRES_USER=kubenews -e POSTGRES_DB=kubenews --network kubenews_net --mount type=volume,source=kubenews_vol,target=/var/lib/postegresql/data postgres:12.17 

# Subindo container da aplicacao
docker container run -d -p 8080:8080 --name kubenews_web --network kubenews_net -e DB_DATABASE=kubenews -e DB_USERNAME=kubenews -e DB_PASSWORD=Pg123 -e DB_HOST=kubenews_db lufertonu/kube-news:v1
    