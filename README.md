# 🛠️ Sistema RH Interno - Arquitetura de Software

Este projeto foi desenvolvido como solução para um sistema interno de **gestão de tarefas do RH** de uma grande empresa de automóveis. O foco é garantir **segurança, controle de acesso, e operação restrita à intranet corporativa**.

---

## 📌 Resumo da Arquitetura

- 💻 Aplicação Web segura, acessada via navegador (thin client).
- 🔐 Controle de acesso com autenticação forte (criptografia de senha, JWT).
- 🧠 Backend desenvolvido com **Kotlin + Spring Boot**.
- 🛡️ Acesso 100% interno (intranet), sem exposição externa.
- 🗄️ Banco de dados relacional seguro (PostgreSQL / Oracle).

---

## 🔷 C4 Model - Diagrama de Contexto (C1)

```mermaid
C4Context
title Sistema RH Interno - Diagrama de Contexto

Person(rh_employee, "Funcionário do RH", "Gerencia tarefas e dados internos do departamento de RH")

System(system_rh, "Sistema RH Interno", "Web Application", "Sistema para controle e gestão de tarefas do RH, acessível somente dentro da intranet da empresa")

rh_employee --> system_rh : Acessa e utiliza para realizar tarefas diárias
