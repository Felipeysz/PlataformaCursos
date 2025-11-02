# 📚 Plataforma de Cursos — Arquitetura Monolítica Modular

## 🗺️ Visão Geral

Sistema único (monolito) desenvolvido em **.NET 9** seguindo princípios de **Clean Architecture** e **DDD (Domain-Driven Design)**.  
Cada módulo é isolado, com suas próprias camadas **Domain**, **Application**, **Infrastructure** e **WebAPI**, facilitando manutenção, escalabilidade e futura migração para microserviços.

## 🧱 Estrutura do Sistema

/src  
├── Auth  
│   ├── Domain  
│   ├── Application  
│   ├── Infrastructure  
│   └── WebAPI  
├── Courses   
├── Content   
├── Enrollment   
├── Payment  
├── Progress   
├── Certificates   
└── Notifications 

**Camadas:**  
* **Domain:** entidades, agregados, regras de negócio puras  
* **Application:** casos de uso, interfaces, DTOs  
* **Infrastructure:** persistência, integrações externas, mensageria  
* **WebAPI:** controllers, endpoints, DTOs de apresentação  

## ⚙️ Tecnologias

* **Linguagem:** C# (.NET 9)  
* **Arquitetura:** Clean Architecture + DDD modular  
* **Banco de Dados:** Azure SQL Database  
* **Cache:** Azure Redis Cache  
* **Armazenamento de mídia:** Azure Blob Storage  
* **Autenticação:** Identity Framework + JWT  
* **Documentação:** Swagger / OpenAPI  
* **Contêinerização:** Docker + Docker Compose  
* **Logs e métricas:** Serilog + Azure Monitor + Application Insights  
* **Testes:** xUnit + FluentAssertions  

## 🧩 Principais Módulos

### 🔐 Auth
Gerencia registro, login, papéis (admin, instrutor, estudante) e emissão de tokens JWT  

### 📚 Courses
CRUD de cursos, módulos e aulas. Permite busca e categorização  

### 🎥 Content
Upload e gerenciamento de vídeos, PDFs e imagens. Metadados armazenados em Azure SQL Database, arquivos em Azure Blob Storage  

### 📝 Enrollment
Gerencia inscrições e permissões de acesso a cursos  

### 💳 Payment
Integração com gateways externos (ex: Stripe, PayPal). Registra transações e confirmações  

### 📈 Progress
Rastreia progresso do aluno  

### 🏆 Certificates
Gera certificados em PDF ao concluir cursos  

### 📢 Notifications
Dispara e-mails e mensagens automáticas baseadas em eventos internos  

## 🧭 Comunicação Interna

Eventos de domínio e handlers são usados para comunicação entre módulos dentro do mesmo processo  

Exemplo:  
* `PaymentCompletedEvent` → cria matrícula  
* `CourseCompletedEvent` → gera certificado  

## 🧰 Observabilidade

* Logs estruturados com **Serilog**  
* Métricas e monitoramento via **Azure Monitor**  
* Telemetria e dashboards com **Application Insights**  

## 📦 Deploy

Executado via Docker Compose:  
* `app` (.NET API)  
* `azure-sql` (Azure SQL Database)  
* `redis` (Azure Redis Cache)  
* `blob-storage` (Azure Blob Storage)  

## ✅ Testes

* Testes unitários e de integração com **xUnit**  
* Mock de dependências com **Moq**  
* Validação de domínio com **FluentAssertions**
