# Modelo
```mermaid
C4Container
title Sistema RH Interno - Diagrama de Contêiner

Person(employee, "Funcionário do RH", "Utiliza o sistema para gerenciar tarefas diárias")

System_Boundary(sistema_rh, "Sistema RH Interno") {
    
    Container(web_browser, "Navegador Web (Thin Client)", "HTML/JavaScript", "Interface do usuário acessada via Intranet")
    
    Container(springboot_app, "Aplicação Backend Kotlin", "Spring Boot", "Exposição da API REST e renderização da interface via servidor")
    
    ContainerDb(database, "Banco de Dados Interno", "PostgreSQL / Oracle", "Armazena informações críticas do sistema RH")

    Container(auth, "Camada de Autenticação", "Spring Security", "Gerencia autenticação, sessões e segurança com criptografia forte")
    
    web_browser --> springboot_app : HTTPS (Intranet)
    springboot_app --> auth : Validação de credenciais / Tokens
    springboot_app --> database : JDBC / JPA (acesso seguro ao banco)
}

employee --> web_browser : Acessa via navegador na rede interna
```
