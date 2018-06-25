# README

## Dependências

- PHP 7.1
- Apache 2.2
- MySQL client 5.7

## Bibliotecas PHP
- php-xml
- php-pdo
- php-mysql
- php-gd

## Como usar

Para usar esse container você precisa primeiro criar um fork ou clonar esse repositório.

Em seguida vá até o arquivo .gitignore na raiz do projeto e remova as linhas seguintes do comentário:

`## Remove this lines when using your project`

Remova esse Readme e faça as alterações necessárias para o seu projeto.

## Instalação

Crie um arquivo .env baseado no example.env.txt

Em seguida rode o docker-compose:

`$ docker-compose up`

> Use o parametro -d para rodar o comando acima sem log

Durante esse processo ele ira criar a imagem, o container e configurar os arquivos baseados nas variaveis do .env criado

## Referencias

[Wodby - Docker-based Wordpress stack](https://github.com/wodby/wordpress-composer)
