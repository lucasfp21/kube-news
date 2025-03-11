# Rodando banco de dados com container:
    docker container run -d -p 5432:5432 -e POSTGRES_PASSWORD=Pg #123 -e POSTGRES_USER=kubedevnews -e POSTGRES_DB=kubedevnews --mount source=kubedevnews_vol,target=/var/lib/postgresql/data postgres

## Nota de experi:
### se voce já criou um volume para usar no postgres mas tomou algum erro na primeira execucao (erro de senha por ex), exclua o volume antigo altera as propriedades no codigo e no comando do container e depois crie um novo volume e passe no comando de execucao do container.
