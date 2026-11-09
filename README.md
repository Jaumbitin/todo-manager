# Todo Manager

Estrutura inicial de uma API de tarefas em **Java 21 e Spring Boot**, com dependências para PostgreSQL, JPA, Flyway, validação e Actuator.

## Estado do projeto

O repositório contém a classe de inicialização, configuração Maven, Docker Compose e testes de contexto. **Ainda não há controllers, entidades de tarefa, serviços, repositórios ou migrações Flyway publicados.** Portanto, não há endpoints de CRUD de tarefas disponíveis nesta versão.

## Requisitos

- JDK 21, com `JAVA_HOME` configurado.
- Docker com Docker Compose disponível.
- Maven Wrapper incluído: `mvnw.cmd` no Windows e `./mvnw` no Linux/macOS.

As versões do Spring Boot e do Maven estão declaradas em `pom.xml` e `.mvn/wrapper/maven-wrapper.properties`.

## Executar para desenvolvimento

```powershell
git clone https://github.com/Jaumbitin/todo-manager.git
cd todo-manager
.\mvnw.cmd spring-boot:run
```

A integração de desenvolvimento do Spring Boot usa `compose.yaml` para iniciar o PostgreSQL. Mantenha o Docker ativo. O Compose publica a porta do banco em uma porta disponível do host; consulte `docker compose ps` para identificá-la.

O Compose atual contém uma senha fixa de desenvolvimento. Substitua-a localmente e não a reutilize em outros serviços ou ambientes. A imagem `postgres:latest` não fixa uma versão do banco.

## Testes

```powershell
.\mvnw.cmd test
```

Os testes usam Testcontainers e precisam de Docker. Eles validam a inicialização do contexto; não comprovam um fluxo de tarefas, que ainda não foi implementado.

## Organização

- `src/main/java/com/todo/todolist/TodolistApplication.java`: inicialização.
- `src/main/resources/application.properties`: nome da aplicação.
- `src/test/`: contexto Spring e configuração PostgreSQL de teste.
- `compose.yaml`: banco de desenvolvimento.
- `pom.xml`: dependências e build.

## Próximos passos

Implementar o domínio de tarefas, migrações, contratos HTTP, validação, tratamento de erros e testes do CRUD. Separar credenciais locais da configuração versionada antes de utilizar dados reais.
