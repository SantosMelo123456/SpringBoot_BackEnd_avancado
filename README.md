# SpringBoot_BackEnd_avancado
Projeto API 

**PROJETO SPRING BOOT - CADASTRO/PESQUISA ALUNO e PROFESSOR**
_________________________________________________________________________________________________________________________________________________________________________________________
inserção do aluno e Professor com informações detalhadas:

O **Aluno Online** é uma API RESTful desenvolvida como projeto acadêmico, com foco na construção de um back-end bem estruturado para o gerenciamento de alunos. O projeto aplica boas práticas de arquitetura em camadas com Spring Boot, separando as responsabilidades entre Controller, Service e Repository.
Projeto desenvolvido durante o 3º semestre do curso de Ciência da Computação.

##Implementações
_________________________________________________________________________________________________________________________________________________________________________________________
### Aluno

* Cadastro de aluno com campos obrigatórios: **nome**, **e-mail** e **CPF**
* Validação de CPF único por aluno
* Retorno do aluno cadastrado com código de identificação gerado automaticamente
* Atualização parcial ou total dos dados do aluno
* Remoção de aluno por ID
* Busca de aluno por ID
* Listagem de todos os alunos cadastrados
* Respostas padronizadas com status HTTP (`200`, `201`, `404`, `400`)

### Professor

* Cadastro de professor com campos obrigatórios: **nome**, **e-mail** e **CPF**
* Validação de CPF único por professor
* Retorno do professor cadastrado com código de identificação gerado automaticamente
* Atualização parcial ou total dos dados do professor
* Remoção de professor por ID
* Busca de professor por ID
* Listagem de todos os professores cadastrados
* Respostas padronizadas com status HTTP (`200`, `201`, `404`, `400`)


## Endpoints da API
_________________________________________________________________________________________________________________________________________________________________________________________
###Endpoints de criação de Alunos/Professores:
- URL: /alunos
- Content-Type: application/json
- Corpo da Requisição: Objeto JSON com os campos obrigatórios: name, email e cpf

| Método | Rota | Descrição |
|---|---|---|
| `POST` | `/alunos` | Cadastra um novo aluno |
| `GET` | `/alunos` | Lista todos os alunos |
| `GET` | `/alunos/{id}` | Busca aluno por ID |
| `PUT` | `/alunos/{id}` | Atualiza dados do aluno |
| `DELETE` | `/alunos/{id}` | Remove um aluno |


## Teste da API de Cadastro de Aluno/Professor no Insomnia
_________________________________________________________________________________________________________________________________________________________________________________________
endpoint: `http://localhost:8080`  
Exemplo de dados no corpo da requisição, informe os dados de um novo paciente em formato JSON.
<img width="1260" height="710" alt="image" src="https://github.com/user-attachments/assets/7d102ffc-afda-4b65-b7b1-b0c00e148743" />
<img width="1262" height="717" alt="image" src="https://github.com/user-attachments/assets/36ff712d-7c98-4334-ab0d-27374243e095" />
<img width="1261" height="708" alt="image" src="https://github.com/user-attachments/assets/0608b8ac-033c-4723-98d4-50b057634a04" />
<img width="1251" height="708" alt="image" src="https://github.com/user-attachments/assets/e9cc9449-90f3-4603-8d56-729087487e76" />
<img width="1265" height="709" alt="image" src="https://github.com/user-attachments/assets/cab9c3cf-6092-464b-8b30-1c5d3adc7496" />
<img width="1206" height="705" alt="image" src="https://github.com/user-attachments/assets/b069ca2e-6aff-4459-affd-71f372a8a0f3" />


## Resposta de Sucesso - exemplo
_________________________________________________________________________________________________________________________________________________________________________________________
<img width="344" height="259" alt="image" src="https://github.com/user-attachments/assets/2d9bd161-8c81-4023-a1b3-e45583284407" />
**buscarAluno**

##  Arquitetura
_________________________________________________________________________________________________________________________________________________________________________________________

O projeto segue o padrão de **arquitetura em camadas (Layered Architecture)**:
src/
└── main/
    └── java/
        └── com/example/alunoonline/
            ├── controller/        ← Recebe as requisições HTTP
            ├── service/           ← Contém as regras de negócio
            ├── repository/        ← Comunicação com o banco de dados (JPA)
            ├── model/             ← Entidades JPA
            └── AlunOnlineApplication.java

| Camada | Responsabilidade |
|---|---|
| `Controller` | Expõe os endpoints REST e delega para o Service |
| `Service` | Aplica as regras de negócio antes de persistir |
| `Repository` | Interface com o banco via Spring Data JPA |
| `Model` | Mapeamento das entidades para o banco de dados |



## Tecnologias utilizadas
_________________________________________________________________________________________________________________________________________________________________________________________

| Tecnologia | Versão | Uso |
|---|---|---|
| Java | 21 (Amazon Corretto) | Linguagem principal |
| Spring Boot | 3.x | Framework web |
| Spring Data JPA | — | Persistência de dados |
| Hibernate | — | ORM (via JPA) |
| Maven | — | Gerenciador de dependências |
| IntelliJ IDEA | — | IDE de desenvolvimento |

##  Funcionalidades implementadas
_________________________________________________________________________________________________________________________________________________________________________________________

- [x] Cadastro de aluno
- [x] Listagem de todos os alunos
- [x] Busca de aluno por ID
- [x] Atualização de dados do aluno
- [x] Remoção de aluno
- [x] Conexão com banco de dados via JPA/Hibernate
- [ ] Documentação Swagger *(em breve)*
- [ ] Tratamento global de exceções *(em breve)*

## Como executar localmente
_________________________________________________________________________________________________________________________________________________________________________________________

### Pré-requisitos

- Java 21+
- Maven instalado
- Banco de dados configurado (MySQL / PostgreSQL)

### Passo a passo

```bash
# 1. Clone o repositório
git clone https://github.com/SantosMelo123456/aluno-online.git

# 2. Entre na pasta do projeto
cd aluno-online

# 3. Configure o banco no arquivo de propriedades
# src/main/resources/application.properties

# 4. Execute o projeto
./mvnw spring-boot:run


### Configuração do banco (`application.properties`)
_________________________________________________________________________________________________________________________________________________________________________________________
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/aluno_online
spring.datasource.username=seu_usuario
spring.datasource.password=sua_senha
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

##  Aprendizados & Desafios
_________________________________________________________________________________________________________________________________________________________________________________________
Durante o desenvolvimento deste projeto, os principais desafios enfrentados foram:

- **Configuração do `pom.xml`** — identificar dependências incorretas (ex: `spring-boot-starter-webmvc` → `spring-boot-starter-web`) e conflitos de versão
- **Arquitetura em camadas** — entender o fluxo correto de dados entre Controller → Service → Repository
- **Anotações JPA** — uso correto de `@Entity`, `@Id`, `@GeneratedValue` e `@Column`
- **Configuração do ambiente** — setup do IntelliJ IDEA com Amazon Corretto 21 e plugin Lombok



final do Projeto Spring - Cadastro Aluno/Professor
