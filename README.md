# Spring Cloud Config Server

Projeto de estudo sobre configuração centralizada usando Spring Cloud Config Server para gerenciar configurações de múltiplas aplicações de forma centralizada.

## 📋 Descrição

Este projeto demonstra a implementação de um servidor de configuração centralizada usando Spring Cloud Config Server, junto com três aplicações cliente que consomem essas configurações:

- **Config Server**: Servidor central de configurações
- **Cliente Estoque**: Aplicação cliente para gerenciamento de estoque
- **Cliente Vendas**: Aplicação cliente para gerenciamento de vendas
- **Cliente Relatórios**: Aplicação cliente para geração de relatórios

## 🏗️ Arquitetura

```
┌─────────────────┐    ┌──────────────────┐
│   Config Server │◄───┤  GitHub Repo     │
│   (Port: 8888)  │    │  (Configurações) │
└─────────┬───────┘    └──────────────────┘
          │
          ▼
┌─────────────────────────────────────────┐
│              Clientes                   │
├─────────────┬─────────────┬─────────────┤
│   Estoque   │   Vendas    │ Relatórios  │
│             │             │             │
└─────────────┴─────────────┴─────────────┘
```

## 🚀 Tecnologias Utilizadas

- **Java 17**
- **Spring Boot 4.0.0**
- **Spring Cloud 2025.1.0-RC1**
- **Spring Cloud Config Server**
- **Spring Cloud Config Client**
- **Spring Boot Actuator**
- **Maven**

## 📁 Estrutura do Projeto

```
Spring_Cloud_Config_Server/
├── Config Server/
│   └── Config-Server/          # Servidor de configuração
├── cliente-estoque/
│   └── cliente-estoque/        # Cliente para estoque
├── cliente-vendas/
│   └── cliente-vendas/         # Cliente para vendas
├── cliente-relatorios/
│   └── cliente-relatorios/     # Cliente para relatórios
└── README.md
```

## ⚙️ Configuração

### Config Server
- **Porta**: 8888
- **Repositório Git**: https://github.com/JoselioJr/repo-configs.git
- **Clone automático**: Habilitado
- **Actuator**: Todos os endpoints expostos

### Clientes
- **Profile ativo**: dev
- **Config Server URL**: http://localhost:8888
- **Actuator**: Todos os endpoints expostos

## 🔧 Como Executar

### 1. Executar o Config Server
```bash
cd "Config Server/Config-Server"
mvn spring-boot:run
```
O servidor estará disponível em: http://localhost:8888

### 2. Executar os Clientes

**Cliente Estoque:**
```bash
cd cliente-estoque/cliente-estoque
mvn spring-boot:run
```

**Cliente Vendas:**
```bash
cd cliente-vendas/cliente-vendas
mvn spring-boot:run
```

**Cliente Relatórios:**
```bash
cd cliente-relatorios/cliente-relatorios
mvn spring-boot:run
```

## 🧪 Testando a Aplicação

### Verificar configurações do servidor
```bash
# Verificar configuração do cliente-estoque no profile dev
curl http://localhost:8888/cliente-estoque/dev

# Verificar configuração do cliente-vendas no profile dev
curl http://localhost:8888/cliente-vendas/dev

# Verificar configuração do cliente-relatorios no profile dev
curl http://localhost:8888/cliente-relatorios/dev
```

### Testar endpoints dos clientes
```bash
# Testar mensagem do cliente (assumindo portas padrão)
curl http://localhost:8080/mensagem
```

## 📊 Endpoints Úteis

### Config Server
- **Health Check**: http://localhost:8888/actuator/health
- **Info**: http://localhost:8888/actuator/info
- **Configurações**: http://localhost:8888/{application}/{profile}

### Clientes
- **Mensagem**: http://localhost:{port}/mensagem
- **Health Check**: http://localhost:{port}/actuator/health
- **Refresh**: http://localhost:{port}/actuator/refresh (POST)

## 📝 Funcionalidades

- ✅ Configuração centralizada
- ✅ Múltiplos profiles (dev, prod, etc.)
- ✅ Refresh dinâmico de configurações
- ✅ Integração com repositório Git
- ✅ Monitoramento via Actuator
- ✅ Clone automático do repositório

## 👨‍💻 Alunos

**[Hugo Machado](https://github.com/Hugo-Machado02), [Joselio Jr](https://github.com/JoselioJr) e [Shayra Kelly](https://github.com/ShayraKelly)**