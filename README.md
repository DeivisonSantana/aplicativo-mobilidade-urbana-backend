<h1 align="center">Mobilidade App Backend</h1>

## Sobre o App

Este app é o backend da aplicação de mobilidade urbana desenvolvido pela equipe de TI da Pen6.

## Tecnologias utilizadas

- PHP 8.5
- Laravel 13

## Requisitos:

- PHP 8.5
- MySQL ou MariaDB
- Redis ou Valet
- Docker instalado

> Em ambientes Windows, é necessário ter instalado o WSL2 e alguma distribuição Linux compatível.

Para o ambiente de desenvolvimento, também é requisito:

- RustFS (Storage S3)
- Mailpit (Servidor de email para testes)

## Iniciando o desenvolvimento

Antes de iniciar o ambiente de desenvolvimento, certifique-se de que o arquivo `.env` está devidamente configurado.

Para iniciar a estrutura do ambiente de desenvolvimento pela primeira vez, inicialize o ambiente Docker:

```sh
docker compose up -d --build
```

Após iniciar o ambiente, faça a instalação dos pacotes PHP necessários, utilizando o container de desenvolvimento:

```sh
docker compose exec -it laravel.test composer install
```

Ao realizar a primeira instalação dos pacotes, já estará disponível para utilizar o utilitário [Laravel Sail](https://laravel.com/docs/13.x/sail).

Este utilitário facilita a interação com a estrutura de desenvolvimento do Docker, além de permitir a execução de outros comandos internamente no Laravel.

O binário do utilitário está localizado em `./vendor/bin/sail`.

Para facilitar a execução do binário, adicione um alias do executável no `~/.zshrc` ou `~/.bashrc` (conforme o shell utilizado pelo sistema):

```sh
alias sail='sh $([ -f sail ] && echo sail || echo vendor/bin/sail)'
```

Ao adicionar o alias, feche e abra o terminal, ou execute o comando `source <caminho do arquivo>`, informando o caminho do arquivo onde foi adicionado o código do alias.

> OBSERVAÇÃO: O `sail` só pode ser utilizado pelo terminal do sistema. Não funciona dentro do devcontainer.

> OBSERVAÇÃO 2: O `sail` só funciona dentro da pasta do projeto.

> OBSERVAÇÃO 3: O Docker não está acessível dentro do devcontainer, então não é possível manipular os containers diretamente de dentro do devcontainer, nem acessá-los. O acesso deve ser feito pelo sistema operacional.

Para iniciar o desenvolvimento do código, com o projeto aberto no VSCode basta executar o comando do VSCode "Dev Containers: Reopen in Container".

O devcontainer facilita a manter o ambiente local limpo e padronizado.

## Pós configuração do ambiente

Após configurar o ambiente de desenvolvimento, é necessário executar alguns comandos para preparar o Laravel para funcionar:

```sh
# Caso esteja dentro do devcontainer
php artisan jwt:secret

# Caso esteja no terminal do sistema
sail artisan jwt:secret
```
