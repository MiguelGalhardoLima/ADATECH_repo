# AdaTech
Este repositório contém o ambiente Dockerizado para o portal do grupo de pesquisa Ada Tech. A estrutura utiliza WordPress, MariaDB (MySQL) e phpMyAdmin para facilitar o desenvolvimento e a implantação.

📋 Requisitos do Sistema
WSL 2 instalado (recomendado Ubuntu 22.04+).

Docker Desktop instalado, configurado para usar o backend do WSL 2 e em execução.

VS Code (opcional, mas recomendado).

🛠️ Como Rodar o Projeto
Siga os passos abaixo no terminal do seu VS Code:

Subir os containers:

Bash
docker compose up -d
Importar o Banco de Dados:
Execute o comando abaixo para carregar as configurações e conteúdos:

Bash
docker exec -i adatech-db-1 mysql -u wordpress -pwordpress wordpress < dump.sql
Nota: A senha é wordpress.

Acessar o Ambiente:

Website: http://localhost:8000

Painel Admin: http://localhost:8000/wp-admin

phpMyAdmin: http://localhost:8080

Credenciais de Acesso:

Usuário Admin: admin

Senha: ADA_TECH@2025**

💾 Manutenção e Backup
Exportando o Projeto (Criar novo Backup)
Se você fez alterações no design ou conteúdo e deseja gerar um novo ponto de restauração:

Bash
docker exec -i adatech-db-1 mysqldump -u root -psomewordpress wordpress > dump.sql
Arquivos Críticos para Migração
Para mover este projeto para outro servidor/máquina, você precisa de apenas 3 itens:

dump.sql (O banco de dados atualizado).

wp-content/ (Pasta que contém temas, plugins e mídias).

docker-compose.yml (Configuração da infraestrutura).

🛑 Gerenciamento do Ciclo de Vida
Parar os containers:

Bash
docker compose stop
Remover containers (mantendo os arquivos):

Bash
docker compose down
Limpeza Total (Apagar containers, volumes e banco de dados):

Bash
docker compose down -v
💡 Observações Técnicas
O container do banco de dados está nomeado como adatech-db-1.

Caso ocorram erros de permissão na pasta wp-content, certifique-se de que o usuário do WSL tem permissão de escrita no diretório local.
