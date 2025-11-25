# Desafio Técnico - Microserviços

## Descrição do Desafio

O objetivo é desenvolver uma aplicação com arquitetura de microserviços para gerenciamento de estoque de produtos e vendas em uma plataforma de e-commerce. O sistema será composto por dois microserviços que se comunicam através de um API Gateway e utilizam RabbitMQ para mensageria.

## Tecnologias Utilizadas

A stack tecnológica inclui .NET Core com C#, Entity Framework para acesso aos dados, arquitetura RESTful, RabbitMQ para comunicação assíncrona, JWT para autenticação, PostgreSQL como banco de dados relacional e API Gateway como orquestrador das requisições.

## Arquitetura Proposta

### Microserviço 1 - Gestão de Estoque

Este microserviço é responsável pelo gerenciamento do catálogo de produtos e níveis de inventário. Suas funcionalidades incluem cadastro de novos produtos com informações como nome, descrição, preço e quantidade disponível. Também oferece consulta do catálogo de produtos com visualização das quantidades em estoque e permite atualização automática dos níveis de estoque quando vendas são processadas.

### Microserviço 2 - Gestão de Vendas

Este microserviço cuida de todo o processo de compra e acompanhamento de pedidos. Realiza a criação de novos pedidos com validação prévia do estoque para garantir que os produtos estejam disponíveis. Permite que os clientes consultem o status de seus pedidos já realizados. Quando uma venda é confirmada, envia um evento através do RabbitMQ para que o estoque seja devidamente reduzido.

### API Gateway

O API Gateway funciona como o único ponto de entrada da aplicação, responsável por rotear todas as requisições para o microserviço apropriado. Desta forma, os clientes não precisam conhecer os endpoints específicos de cada serviço.

### RabbitMQ

A comunicação entre os microserviços ocorre de forma assíncrona através do RabbitMQ. Quando uma venda é realizada, um evento é publicado no broker de mensagens para que o serviço de estoque possa processar a redução de quantidade de forma desacoplada.

### Autenticação com JWT

A aplicação implementa autenticação por tokens JWT. Apenas usuários autenticados podem realizar vendas ou consultar informações do estoque, garantindo segurança no acesso aos recursos sensíveis.

## Status Atual

O projeto foi finalizado com sucesso e encontra-se em fase de refinamento da sintaxe do código. Testes automatizados estão em desenvolvimento para validar o comportamento dos microserviços.

## Estrutura Básica

A organização dos diretórios segue um padrão bem definido com pasta BD para scripts e configurações de banco de dados, Contexto para as classes de contexto do Entity Framework, Controllers para os endpoints da API, DTOs para transferência de dados entre camadas, Migrations para controle de versão do schema, e RabbitMQ para configurações de mensageria. Os arquivos principais Program.cs e appsettings.json completam a estrutura base.
