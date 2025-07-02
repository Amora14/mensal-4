# Projeto ResiHub v.01- Full Stack com Java e Angular

# 📝 Visão Geral do Projeto
ResiHub é um sistema de gerenciamento de apartamentos, criado inicialmente pensando em pequenos administradores, o sistema realiza as principais funções como listagem de apartamentos, cadastro de clientes e contrados. 

# 💻 Tecnologias Utilizadas
Backend: Java com Spring Boot

Frontend: Angular

Banco de Dados: MySQL

Containers: Docker

Orquestração: Kubernetes

# 🚀 Estrutura do Projeto
## 🔙 Backend (Java & Spring Boot)
O coração da aplicação. O backend é responsável por toda a lógica de negócio e foi desenvolvido utilizando Java e o framework Spring Boot. Suas principais funções são:

API RESTful: Disponibiliza um conjunto de endpoints seguros para o frontend acessar os dados da aplicação (cadastrar, consultar, editar e excluir).

Regras de Negócio: Centraliza toda a lógica, validações e processamento de dados.

Gerenciamento de Dados: Através do Spring Data JPA, ele se comunica de forma eficiente com o banco de dados MySQL para realizar todas as operações de persistência.

Observação: Você mencionou "Spring Boot 17". Geralmente, o comum é usar Java 17 com uma versão do Spring Boot como a 2.x ou 3.x. Este backend está configurado para ser performático e seguro, aproveitando todo o ecossistema Spring.

## 🖥️ Frontend (Angular)
O frontend é a camada de apresentação, a interface com a qual o usuário final interage. Desenvolvido com Angular, ele proporciona uma experiência de usuário rica e reativa (Single Page Application - SPA).

Interface Dinâmica: Constrói componentes reutilizáveis para criar uma interface moderna e fácil de usar.

Consumo de API: Utiliza o serviço HttpClient do Angular para se comunicar com a API do backend, enviando e recebendo dados de forma assíncrona.

Gerenciamento de Estado: Controla o estado da aplicação para manter a interface consistente e atualizada em tempo real.

## 🗃️ Banco de Dados (MySQL)
Para o armazenamento de dados, o projeto utiliza o MySQL, um dos sistemas de gerenciamento de banco de dados relacionais mais populares e confiáveis do mundo.

Armazenamento Estruturado: Organiza todas as informações da aplicação em tabelas, garantindo a integridade e a consistência dos dados.

Persistência: Garante que os dados sejam salvos de forma segura e permanente.

## 🐳 Docker
O Docker empacota a aplicação do frontend e backend para criar as imagens.

DockerHub: usado como repositório das imagens.


## ☸️ Kubernetes
O Kubernetes entra em cena para automatizar e gerenciar a implantação da nossa aplicação em um ambiente de produção. Ele garante que o backend, o frontend e o banco de dados funcionem de maneira coesa e escalável.

Orquestração de Contêineres: Gerencia os contêineres Docker da API (Java) e do App (Angular).

Alta Disponibilidade: Garante que a aplicação esteja sempre no ar, reiniciando contêineres que falham e distribuindo a carga entre eles.

Service Discovery e Load Balancing: Permite que o frontend encontre e se comunique com o backend de forma simples e que o tráfego seja distribuído eficientemente.

Como Executar
Para rodar este projeto, você precisará ter o Docker e o Kubernetes (Minikube, Docker Desktop, etc.) configurados.

Construa as imagens Docker de cada aplicação (backend e frontend).

Bash

# Exemplo para o backend Spring Boot
./mvnw spring-boot:build-image -Dspring-boot.build-image.imageName=seu-usuario/backend-api

# Exemplo para o frontend Angular
docker build -t seu-usuario/frontend-app .
Aplique os manifestos do Kubernetes para implantar a aplicação:

Bash

kubectl apply -f /caminho/para/seus/manifestos/kubernetes/
