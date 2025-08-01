# 🚀 PHP Docker

Este script automatiza a configuração de um ambiente de desenvolvimento PHP completo com Docker, incluindo Apache, PHP, MySQL, Redis, phpMyAdmin e MailHog. Ideal para iniciar novos projetos rapidamente e manter a consistência entre diferentes ambientes de desenvolvimento.

## ✨ Funcionalidades

Este script oferece as seguintes funcionalidades principais:

*   **Ambiente Completo:** Configura um ambiente de desenvolvimento PHP com 🐘 Apache, 🌐 PHP, 🗄️ MySQL, ⚡ Redis, 📊 phpMyAdmin e 📧 MailHog.
*   **Automatização Total:** Automatiza a criação de toda a estrutura de diretórios e arquivos de configuração Docker.
*   **Gerenciamento de Versões PHP:** Permite alternar facilmente entre diferentes versões do PHP.
*   **Gerenciamento de Banco de Dados:** Inclui scripts para backup e restauração do MySQL.
*   **Estrutura de Projeto Organizada:** Cria uma estrutura de pastas lógica para o seu projeto PHP.
*   **Scripts de Gerenciamento:** Fornece um script `manage.sh` para controlar os serviços Docker de forma simples.
*   **Exemplos Iniciais:** Gera arquivos de aplicação de exemplo para um início rápido.

## 📋 Requisitos

Para utilizar este script, você precisará ter os seguintes softwares instalados em seu sistema:

*   **[Docker](https://www.docker.com/get-started/)**: Plataforma para desenvolver, enviar e executar aplicativos usando contêineres.
*   **[Docker Compose](https://docs.docker.com/compose/install/)**: Ferramenta para definir e executar aplicativos Docker multi-contêiner.

### Verificando a Instalação

Você pode verificar se o Docker e o Docker Compose estão instalados corretamente executando os seguintes comandos no seu terminal:

```bash
docker --version
docker-compose --version
```

Se eles não estiverem instalados, siga os links acima para as instruções de instalação oficiais.

## 📦 Instalação

1.  **Clone o repositório (ou baixe o script `setup_project.sh`):**

    ```bash
    git clone https://github.com/jhonatanMP/php-doker.git
    cd seu-repositorio
    ```

2.  **Dê permissão de execução ao script:**

    Antes de executar o script, você precisa conceder permissões de execução a ele. Abra seu terminal e navegue até o diretório onde o script `setup_project.sh` está localizado e execute:

    ```bash
    chmod +x setup_project.sh
    ```

## 🛠️ Uso

Após conceder as permissões de execução, você pode executar o script da seguinte forma:

```bash
./setup_project.sh
```

O script irá:

1.  **Solicitar o nome do projeto:** Este nome será usado para criar o diretório principal do projeto e para configurar nomes de contêineres e bancos de dados.
2.  **Criar a estrutura de diretórios:** Uma estrutura de pastas organizada será criada para o seu projeto PHP, incluindo `src/public`, `src/app`, `docker/apache`, `mysql/init`, entre outros.
3.  **Gerar arquivos de configuração:** Arquivos essenciais como `Dockerfile`, `docker-compose.yml`, `.env`, `php.ini` e a configuração padrão do Apache (`000-default.conf`) serão criados e pré-configurados.
4.  **Configurar o MySQL:** Um script SQL inicial (`mysql/init/init.sql`) será gerado para criar o banco de dados e um usuário com as permissões necessárias, além de uma tabela de exemplo.
5.  **Criar arquivos de aplicação de exemplo:** Arquivos como `index.php`, `phpinfo.php` e `test-db.php` serão criados em `src/public` para você ter um ponto de partida e testar o ambiente.
6.  **Gerar o script de gerenciamento (`manage.sh`):** Este script auxiliará no controle dos contêineres Docker (iniciar, parar, reiniciar, logs, etc.).

### Iniciando o Ambiente

Após a execução bem-sucedida do `setup_project.sh`, navegue até o diretório do seu novo projeto e inicie os contêineres Docker:

```bash
cd seu-nome-do-projeto
./manage.sh start
```

Isso irá construir as imagens Docker (se necessário) e iniciar todos os serviços definidos no `docker-compose.yml`.

### Acessando a Aplicação

Uma vez que os contêineres estejam em execução, você poderá acessar sua aplicação e os serviços auxiliares:

*   **Aplicação PHP:** `http://localhost:8080`
*   **phpMyAdmin:** `http://localhost:8081`
*   **MailHog:** `http://localhost:8025`

### Outros Comandos Úteis (`manage.sh`)

O script `manage.sh` oferece diversos comandos para gerenciar seu ambiente:

*   `./manage.sh stop`: Para todos os contêineres.
*   `./manage.sh restart`: Reinicia todos os contêineres.
*   `./manage.sh status`: Mostra o status dos contêineres.
*   `./manage.sh logs [serviço]`: Exibe os logs de um serviço específico (ex: `php-app`, `mysql`).
*   `./manage.sh exec [comando]`: Executa um comando dentro do contêiner PHP (ex: `./manage.sh exec php -v`).
*   `./manage.sh composer [args]`: Executa comandos do Composer dentro do contêiner PHP (ex: `./manage.sh composer install`).
*   `./manage.sh switch [versão]`: Troca a versão do PHP (ex: `./manage.sh switch 8.1`).
*   `./manage.sh backup`: Cria um backup do banco de dados MySQL.
*   `./manage.sh restore [arquivo]`: Restaura um backup do banco de dados MySQL.
*   `./manage.sh clean`: Remove todos os contêineres, imagens e volumes Docker associados ao projeto (use com cautela!).

## 💻 Executando em Diferentes Sistemas Operacionais

O script `setup_project.sh` foi projetado para ser compatível com os principais sistemas operacionais que suportam Docker.

### 🍎 macOS & 🐧 Linux

Para usuários de macOS e Linux, a execução do script é direta através do terminal:

1.  Abra o Terminal.
2.  Navegue até o diretório onde você salvou o script `setup_project.sh`.
3.  Conceda permissão de execução:
    ```bash
    chmod +x setup_project.sh
    ```
4.  Execute o script:
    ```bash
    ./setup_project.sh
    ```

### 🪟 Windows (WSL)

Para usuários de Windows, é altamente recomendado utilizar o [Windows Subsystem for Linux (WSL)](https://docs.microsoft.com/pt-br/windows/wsl/) para executar o script. O WSL oferece um ambiente Linux completo dentro do Windows, garantindo a compatibilidade total com as ferramentas de linha de comando e o Docker.

1.  **Instale o WSL e uma distribuição Linux (ex: Ubuntu):** Siga as instruções oficiais da Microsoft para instalar e configurar o WSL.
2.  **Instale o Docker Desktop para Windows:** Certifique-se de que o Docker Desktop esteja configurado para usar o backend WSL 2.
3.  **Abra o terminal WSL:** Inicie sua distribuição Linux instalada (ex: Ubuntu) a partir do menu Iniciar.
4.  **Navegue até o diretório do script:** Dentro do terminal WSL, navegue até o diretório onde você salvou o script `setup_project.sh`.
5.  **Conceda permissão de execução:**
    ```bash
    chmod +x setup_project.sh
    ```
6.  **Execute o script:
    ```bash
    ./setup_project.sh
    ```

## 🤝 Contribuição

Contribuições são sempre bem-vindas! Se você tiver sugestões de melhoria, encontrar bugs ou quiser adicionar novas funcionalidades, sinta-se à vontade para abrir uma *issue* ou enviar um *pull request* no repositório do GitHub.

## 📄 Licença

Este projeto está licenciado sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.



