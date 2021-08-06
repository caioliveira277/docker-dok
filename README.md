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
* **Hosts:** 🌐<br>
    Tenha o arquivo de **hosts** com as entradas abaixo:
    ```vim
    127.0.0.1       dok.site
    127.0.0.1       dok.checkout
    127.0.0.1       dok.painel
    127.0.0.1       dok.consultas
    127.0.0.1       dok.email-marketing
    ```
    Caminho do arquivo no **Windows**: `C:\Windows\System32\drivers\etc`<br>
    Caminho do arquivo no **Linux**: `/etc/hosts`<br>

### Instalando projetos

1. Clone o repositório:
   ```sh
   git clone https://github.com/caioliveira277/docker-dok.git
   ```
   <br>
   
2. Clone os projetos em suas pastas correspondentes:
    >***Exemplo***: <br>
    O projeto dok-site-novo será clonado na pasta dok-site-novo representado na estrutura abaixo
   ```sh
    .
    ├── .docker
    │   └── mysql
    ├── dok-site-novo
    │   ├── dok-site-novo *projeto*
    │   ├── Dockerfile
    │   └── vhost.conf
    ├── .env
    ├── .gitignore
    ├── docker-compose.yaml
    └── README.md
    ```
    <small>***Estrutura de pastas do projeto***</small>
    <br>
    
3. Configurando o `.env` do projeto: <br>
    Dentro da pasta do projeto clonado, você encontrará um arquivo chamado `.env.example`, **copie o conteúdo** salvando em um **novo arquivo** chamado `.env` e siga as etapas abaixo:

    >Substitua os parametros de conexão do banco, para o representado abaixo:
    >```sh
    >DB_HOST=${DB_HOST}
    >DB_PORT=${DB_PORT}
    >DB_DATABASE=${DB_DATABASE}
    >DB_USERNAME=${DB_USERNAME}
    >DB_PASSWORD=${DB_PASSWORD}
    >```
    ><small>******</small>
    
    <small>***Exemplo para o host dok.site***</small>
    <br>

4. Inicializando os **containers**: <br>
    Na **raiz desse projeto**, onde encontra-se o arquivo `docker-compose.yaml`, rode o comando abaixo para inicializar os containers configurados:
    ```sh
    docker-compose up -d
    ```
    >***Obs:*** <br>
    >1- A flag `-d` utilizada no comando acima, representa a execução do projeto em modo **daemon**, isso significa que ele rodará em background no sistema operacional. <br><br>
    >2- A flag `--build` pode ser usada caso haja alguma alteração nos arquivos `Dockerfile`, fazendo a reconstrução do container, lendo as novas alterações.
    <br>

5. Projetos em execução: 🚀<br>
    Ao executar o comando da **etapa 4**, será apresentado logs de execução informando se tudo ocorreu bem durante o processo. Isso significa que você poderá partir para a configuração específica de cada projeto, tendo disponível as ferramentas necessárias para funcionamento. **Ex**: `composer, php, node, npm...`
    <br>

    <br>


### Configurando projetos:

Agora que os containers estão rodando, devemos realizar as configurações específicas de cada projeto instalado que será descrito nas etapas abaixo.
>**Obs:** <br>
>O exemplo abaixo utiliza como exemplo o projeto **dok-site-novo** para realizar a configuração.

1. Acessando o terminal do container<br>
    Execute o comando abaixo para acessar o terminal do container pelo nome definido:
    ```sh
    docker exec -i -t dok_site_novo /bin/bash
    ```
    <br>

2. Instalando dependencias:<br>
    >**Composer**<br>
    >Execute o comando de instalação de dependencias do **php**
    >```sh
    >composer install
    >```
    ><small>******</small>

    >**NPM**<br>
    >Execute o comando de instalação de dependencias do **node**
    >```sh
    >npm install
    >```
    ><small>******</small>
    <br>

3. Gerando a **key** do projeto:<br>
    Execute o comando para gerar a chave necessária de aplicações **laravel**
    ```sh
    php artisan key:generate 
    ```
    <br>

4. Gerando estrutura do banco de dados:<br>
    [**SOMENTE AO PROJETO `DOK-SITE-NOVO`**]<br>
    Execute o comando para subir estrutura de tabelas do banco e dados seeder
    ```sh
    php artisan migrate
    ```
    ```sh
    php artisan db:seed
    ```
    <br>

5. Definindo permissão dos logs:<br>
    Execute o comando para definir a permissão de escrita e leitura aos arquivos de logs do **laravel**
    ```sh
    chmod -R 777 /var/www/html/storage/
    ```
    <br>

6. Compilando **assets** do projeto:<br>
    [**SOMENTE AOS PROJETOS `DOK-SITE-NOVO`, `DOK-CHECKOUT` E `DOK-PAINEL`**]<br>
    Execute o comando para deixar o servidor em modo `watch` para **compilar** os arquivos do projeto:
    ```sh
    npm run watch
    ```
    <br>

### Uso:

Após a conclusão dos passos indicados acima, você terá um ambiente de desenvolvimento configurado e gerenciado pelo docker-compose para cada projeto.<br>
Abaixo, segue os passos para subir os containers e deixá-los em modo de desenvolvimento:<br>

>**Iniciando containers**<br>
>Execute o comando do **docker-compose** para subir todos os containers configurados
>```sh
>docker-composer up -d
>```
><small>******</small>
<br>

>**Deixando projeto em modo desenvolvimento**<br>
>Execute o comando para acessar o terminal do container desejado e em seguida execute o comando de modo desenvolvimento
>```sh
>docker exec -i -t dok_site_novo /bin/bash
>```
>```sh
>npm run watch
>```
><small>******</small>
<br>

***Exemplo para o projeto dok-site-novo***


## Time de desenvolvimento
### **DOK Despachante**

Site: [DOK Despachante](https://www.despachantedok.com.br/)

## Licença

Este projeto está licenciado sob a licença [MIT] - consulte o arquivo LICENSE.md para obter detalhes