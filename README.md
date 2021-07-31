# **Docker-dok**
## Projetos **DOK Despachante** em ambiente **docker**

<br>
<p float="left">
<img src="https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white">
<img src="https://img.shields.io/badge/MySQL-00000F?style=for-the-badge&logo=mysql&logoColor=white">
<img src="https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white">
<img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white">
</p>
<br>

<!-- GETTING STARTED -->
## Começando:

Esse projeto foi desenvolvido com o objetivo de facilitar a configuração do ambiente de desenvolvimento utilizando o docker

### Pré-requisitos

Abaixo estará as ferramentas necessárias para rodar o projeto
* **Docker** 🐳<br>
  [Guia de instalação docker](https://docs.docker.com/get-docker/).
* **Docker Compose** 🐳<br>
  [Guia de instalação docker compose](https://docs.docker.com/compose/install/).

### Instalação geral dos projetos

1. Clone o repositório:
   ```sh
   git clone https://github.com/caioliveira277/docker-dok.git
   ```
2. Clone os projetos em suas pastas correspondentes:
    >***Exemplo***: <br>
    O projeto dok-site-novo será clonado na pasta dok-site-novo representado na estrutura abaixo
   ```shell
    .
    ├── .docker
    │   └── mysql
    ├── dok-site-novo
    │   ├── dok-site-novo [projeto]
    │   ├── Dockerfile
    │   └── vhost.conf
    ├── dok-site-novo
    ├── .env
    ├── .gitignore
    ├── docker-compose.yaml
    └── README.md
    ```
    <small>***Estrutura de pastas do projeto***</small>
    <br><br>
    
3. Configurando o `.env` do projeto: <br>
    Após clonar o projeto na sua devida pasta, crie o arquivo `.env` requerido pelo **laravel** em sua configuração inicial. <br>
    **Copie** o conteúdo do `.env.exemple` para o `.env` e faça as alterações em abaixo:

    >Substitua as variaveis de conexão do banco de dados para as variaveis apresentadas abaixo:
    >```sh
    >DB_HOST=${DB_HOST}
    >DB_PORT=${DB_PORT}
    >DB_DATABASE=${DB_DATABASE}
    >DB_USERNAME=${DB_USERNAME}
    >DB_PASSWORD=${DB_PASSWORD}
    >```
    > Altere as variáveis abaixo de acordo com o seu host configurado:
    >```sh
    >APP_URL=http://dok.site
    >APP_DOMAIN=dok.site
    >```
    ><small>***Exemplo para o host dok.site***</small>

    <br>

