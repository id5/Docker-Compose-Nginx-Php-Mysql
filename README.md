# Descrição
Docker utilizando o compose, arquivo de configuração com variáveis de ambiente, criando um container nginx 1.13.3 e um container php 7.1.9-fpm ligados através de um link e criando um container mysql 5.7.19.

# Configuração Container Nginx

1. Exposição de portas

	80 e 443

2. Volume (Obs: verificar se na configuração do docker -> drivers compartilhados, as unidades c: e/ou d: estão habilitadas)

	Aplicação: legba/html -> /var/www/html
	
	Logs: legba/logs -> /var/log/nginx
	
	Virtual Host: legba/sites -> /etc/nginx/conf.d
	
3. Virtual Host

	Criação do vhost modelo http://legba.dev (vhost modificável)

# Configuração Container Php

1. Exposição de portas

	9000

2. Volume (Obs: verificar se na configuração do docker -> drivers compartilhados, as unidades c: e/ou d: estão habilitadas)

	Aplicação: legba/html -> /var/www/html
	
3. Bibliotecas

	Habilitação de bibliotecas do php através de arquivo de configuração. Ex: MBSTRING, GD, MCRYPT, PDO_MYSQL, etc.
	
# Configuração Container Mysql

1. Exposição de portas

	3306

2. Volume (Obs: verificar se na configuração do docker -> drivers compartilhados, as unidades c: e/ou d: estão habilitadas)

	Aplicação: mysql/data -> /var/lib/mysql

3. Configuração para conexão

	- MYSQL_DATABASE      = default
	
    - MYSQL_USER          = default
	
    - MYSQL_PASSWORD      = secret
	
    - MYSQL_ROOT_PASSWORD = root
	
    - MYSQL_PORT          = 3306
	
# Como utitilizar

1. Clone o repositório usando o comando:

   git clone https://github.com/id5/Docker-Compose-Nginx-Php-Mysql

2. Entre na pasta Docker-Compose-Nginx-Php-Mysql e copie o arquivo env-example para .env.

	cp env-example .env

3. Rode seu container:

docker-compose up -d

Projeto baseado em https://github.com/danielnogueira-dev/Docker-Compose-Nginx-Php-Mysql