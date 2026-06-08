# 💊 FarmaVida API - Sistema de E-Commerce para Farmácia

[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen)](https://spring.io/projects/spring-boot)
[![Java](https://img.shields.io/badge/Java-17%2B-orange)](https://docs.oracle.com/en/java/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-blue)](https://www.mysql.com/)
[![JWT](https://img.shields.io/badge/JWT-Authentication-black)](https://jwt.io/)

Uma API RESTful robusta desenvolvida para gerenciar as operações de um e-commerce do nicho farmacêutico. O projeto simula o ecossistema completo de uma farmácia online, abrangendo desde o controle de categorias e produtos até camadas de segurança e autenticação de usuários.

Este projeto representa o consolidado final de bloco focado no desenvolvimento backend escalável, aplicando boas práticas de arquitetura de software, Clean Code e padrões REST.

---

## 🎯 Regras de Negócio & Arquitetura Relacional

O banco de dados foi modelado seguindo uma ordem lógica de dependências, garantindo a integridade referencial desde a inicialização.

* **Relacionamento Robusto:** Vínculo de integridade física e lógica entre as tabelas de `Produtos`, `Categorias` e `Usuarios` utilizando relacionamentos controlados pelo JPA/Hibernate (`@ManyToOne` / `@OneToMany`).
* **Segmentação Dinâmica:** A estrutura foi desenhada para permitir a classificação de diferentes tipos de produtos (como medicamentos ou cosméticos) de forma flexível diretamente através dos atributos no momento do cadastro, sem a necessidade de separação rígida no código.

---

## 🔐 Segurança & Autenticação (Spring Security + JWT)

A proteção de dados e o controle de acesso foram implementados utilizando as especificações mais recentes do ecossistema **Spring Security**, blindando a API contra acessos não autorizados:
* **Criptografia de Senhas:** Utilização do algoritmo `BCryptPasswordEncoder` para garantir o armazenamento seguro das credenciais dos usuários no banco de dados.
* **Autenticação Stateless (JWT):** Geração, validação e controle de tempo de expiração de Tokens JWT (*JSON Web Tokens*), permitindo uma arquitetura moderna e segura para o tráfego de requisições.
* **Gerenciamento Customizado:** Implementação própria da interface `UserDetailsService` (via `UserDetailsServiceImpl`) injetada centralizadamente na classe `SecurityConfig`, isolando e otimizando o fluxo de carregamento de credenciais na memória do Spring.

---

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Java
* **Framework Principal:** Spring Boot (Spring Web, Spring Data JPA, Spring Security)
* **Banco de Dados:** MySQL (Persistência e modelagem relacional)
* **Segurança:** JSON Web Token (JWT) & BCrypt
* **Ferramentas de Teste:** Insomnia (Validação de Endpoints e payloads JSON)

---

## 📈 Endpoints Principais (CRUD Controlado)

A API disponibiliza cobertura total de manipulação de dados através de todos os verbos HTTP para as três entidades mapeadas:

### 👤 Usuários (`/usuario`)
* `POST /usuario/cadastrar` - Registra um novo usuário no sistema com senha criptografada.
* `POST /usuario/logar` - Autentica um usuário e gera o token de acesso JWT.
* `GET /usuario` - Retorna a lista geral de todos os usuários cadastrados.
* `GET /usuario/{id}` - Filtra e localiza um usuário específico através do ID.
* `PUT /usuario` - Atualiza as informações cadastrais de um usuário existente.

### 📂 Categorias (`/categoria`)
* `GET /categoria` - Lista todas as categorias cadastradas no e-commerce.
* `GET /categoria/{id}` - Filtra uma categoria pelo seu identificador único.
* `GET /categoria/descricao/{descricao}` - Busca categorias por correspondência de texto na descrição.
* `POST /categoria` - Cria uma nova categoria logística no sistema.
* `PUT /categoria` - Modifica os dados ou parâmetros de uma categoria existente.
* `DELETE /categoria/{id}` - Remove de forma definitiva uma categoria do banco de dados.

### 📦 Produtos (`/produto`)
* `GET /produto` - Retorna a listagem completa de todos os produtos do catálogo.
* `GET /produto/{id}` - Localiza um produto específico utilizando o ID do banco.
* `GET /produto/produto/{produto}` - Realiza buscas lógicas filtrando pelo atributo nominal do produto.
* `POST /produto` - Insere um novo produto associando-o obrigatoriamente a uma categoria existente.
* `PUT /produto` - Atualiza dados cadastrais e os vínculos de relacionamento de um produto.
* `DELETE /produto/{id}` - Remove fisicamente um item do catálogo de estoque.

---

## 🚀 Como executar o projeto localmente

1. Clone o repositório:
   ```bash
   git clone [https://github.com/seu-usuario/nome-do-repositorio.git](https://github.com/seu-usuario/nome-do-repositorio.git)

2. Configure as credenciais do seu banco de dados MySQL no arquivo src/main/resources/application.properties.

3. Certifique-se de criar o banco de dados local executando:

CREATE DATABASE nome_do_seu_banco;

4. Execute a aplicação através da sua IDE de preferência (STS, IntelliJ ou Eclipse) ou via terminal utilizando o Maven.