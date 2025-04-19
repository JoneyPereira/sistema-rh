## 🛠️ Sistema RH Interno - Arquitetura de Software

Este projeto foi desenvolvido como solução para um sistema interno de **gestão de tarefas do RH** de uma grande empresa de automóveis. O foco é garantir **segurança, controle de acesso, e operação restrita à intranet corporativa**.

---

## 📌 Resumo da Arquitetura

- 💻 Aplicação Web segura, acessada via navegador (thin client).
- 🔐 Controle de acesso com autenticação forte (criptografia de senha, JWT).
- 🧠 Backend desenvolvido com **Kotlin + Spring Boot**.
- 🛡️ Acesso 100% interno (intranet), sem exposição externa.
- 🗄️ Banco de dados relacional seguro (PostgreSQL / Oracle).

---

## 🔷 Diagrama de Contexto (C1)

```mermaid
graph TD
    RH[Funcionário do RH] -->|Acessa via Intranet| Sistema[<b>Sistema RH Interno</b><br/>Gerencia tarefas do RH<br/>Acesso interno e seguro]
```

---

## 🧱 Diagrama de Contêiner (C2)

```mermaid
graph TD
    A[Funcionário do RH] --> B[Navegador Web (Thin Client)]
    B --> C[Aplicação Backend - Spring Boot (Kotlin)]
    C --> D[Camada de Autenticação - Spring Security]
    C --> E[Banco de Dados Interno<br/>(PostgreSQL/Oracle)]
```

---

## 🧩 Diagrama de Componentes (C3)

```mermaid
graph TD
    Subsystem[Spring Boot App] --> Controller[Controllers - Spring Web]
    Controller --> Service[Serviços - Lógica de Negócio]
    Service --> Repository[Repositórios - Spring Data JPA]
    Service --> Security[Segurança - JWT + Criptografia]
```

---

## 🧬 Diagrama de Código (C4)

```mermaid
classDiagram
    class UserController {
        +createUser(request: UserDTO): ResponseEntity<UserDTO>
        +getUser(id: Long): ResponseEntity<UserDTO>
        +login(credentials: LoginDTO): ResponseEntity<TokenDTO>
    }

    class UserService {
        +createUser(userDTO: UserDTO): User
        +getUserById(id: Long): User
        +authenticate(loginDTO: LoginDTO): TokenDTO
    }

    class UserRepository {
        +findById(id: Long): Optional<User>
        +findByUsername(username: String): Optional<User>
        +save(user: User): User
    }

    class User {
        -id: Long
        -username: String
        -password: String
        -role: String
    }

    class LoginDTO {
        -username: String
        -password: String
    }

    class TokenDTO {
        -token: String
        -expiresIn: Long
    }

    UserController --> UserService
    UserService --> UserRepository
    UserRepository --> User
    UserService --> LoginDTO
    UserService --> TokenDTO
```

---
