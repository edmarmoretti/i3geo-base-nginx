# i3Geo Softwate básico com FastCgi e Nginx
[![Docker Build Statu](https://img.shields.io/docker/build/i3geo/i3geo-base-nginx.svg)](https://hub.docker.com/r/i3geo/i3geo-base-nginx/builds/)
[![Docker Pulls](https://img.shields.io/docker/pulls/i3geo/i3geo-base-nginx.svg)](https://hub.docker.com/r/i3geo/i3geo-base-nginx/builds/)

O objetivo desta imagem Docker é prover o software básico, com FstCgi (php-fpm) para utilização do i3Geo. Para o desenvolvedor este é um mecanismo que apoia o processo de criação de novas funcionalidades uma vez que todas as dependencias já estão instaladas.

Para utilizar em modo de desenvolvimento:

*  Instale a última versão do Docker em seu computador;
*  Faça checkout do i3geo a partir do gitHub;
*  Entre na pasta onde está o código;
*  Digite o comando `docker run -it -p 80:8080 -v $PWD:/var/www/i3geo --rm i3geo/i3geo-base-nginx`

Após docker ser executado, o console já está dentro do contêiner, agora digite:

*  Copia as variáveis de ambiente `/bin/bash -c 'source /php-fpm-envvar.sh'`
*  Inicie o nginx `service nginx start`


Acesse navegador e digite `http://localhost/i3geo`

A conexão com o banco de dados pode ser definida por meio de variáveis de ambiente, exemplo:

`docker run -it -e DB_HOST='postgres-local.app' -e DB_PORT='5432' -e DB_DATABASE='postgres' -e DB_USER='postgres' -e DB_PASSWORD='postgres' -p 80:8080 -v $PWD:/var/www/i3geo --rm i3geo/i3geo-base-nginx`

Os comandos `run` dos exemplos fazem com que o usuário entre na instância da imagem i3geo já com o código no DOC_ROOT do apache, sendo assim, basta escolher o editor de sua preferência e alterar o código em sua máquina e não dentro do contêiner docker.
