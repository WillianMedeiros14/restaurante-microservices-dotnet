## Sobre o Projeto 🚀

Este projeto consiste em uma aplicação de microservices para gerenciamento de um restaurante, utilizando tecnologias modernas e um design orientado a serviços. Ele inclui serviços como ItemService e RestauranteService, responsáveis por diferentes domínios da aplicação, permitindo a escalabilidade e a independência entre os módulos. A comunicação entre os serviços é facilitada pelo RabbitMQ, que atua como um intermediário para o envio e recebimento de mensagens.

## Tecnologias Utilizadas 🛠️

As principais tecnologias e bibliotecas utilizadas no projeto incluem:

- **.NET Core 6.0**
- **MySql** como banco de dados.
- **Swagger** para documentação da API.
- **AutoMapper** para mapeamento de objetos.

---

## Pré-requisitos 📋

Antes de começar, certifique-se de ter o seguinte instalado em seu ambiente:

- [.NET SDK](https://dotnet.microsoft.com/download) (versão 6.0)
- [Docker](https://www.docker.com/) configurado
- [Git](https://git-scm.com/) para controle de versão

---

## Configuração do Ambiente ⚙️

1. Clone o repositório:

   ```bash
   https://github.com/WillianMedeiros14/restaurante-microservices-dotnet.git
   cd restaurante-microservices-dotnet
   ```

## Rodando a Aplicação ▶️

- RabbitMQ:

  ```bash
  # rodar no terminal em qualquer pasta
  docker run -d --hostname rabbitmq-service --name rabbitmq-service --network restaurante-bridge rabbitmq:3-management
  ```

- MySql:

  ```bash
  # rodar no terminal em qualquer pasta
  docker run --name=mysql -e MYSQL_ROOT_PASSWORD=root -d --network restaurante-bridge mysql:5.6
  ```

- ItemService:

  ```bash
  # Entre na pasta
  cd ItemService

  # buidar a api coom docker
  docker build -t itemservice:1.1 .

  # rodar
  docker run --name=item-service -p 8080:80 --network restaurante-bridge itemservice:1.1
  ```

- RestauranteService:

  ```bash
  # Entre na pasta
  cd RestauranteService

  # buidar a api coom docker
  docker build -t restauranteservice:1.1 .

  # rodar
  docker run --name=restaurante-service -p 8081:80 --network restaurante-bridge restauranteservice:1.1
  ```

## Swagger

Depois de rodar as aplicações, elas estarão disponíveis em:

- ItemService: http://localhost:8080/swagger/index.html
- RestauranteService: http://localhost:8081/swagger/index.html
