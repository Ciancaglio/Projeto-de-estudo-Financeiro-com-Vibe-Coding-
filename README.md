# EcoFuel – Documentação Completa

A seguir estão: PRD, Personas, Fluxos, Jornada, Wireframes, Arquitetura, Modelo de Dados, APIs, Plano de Validação, Testes e README.

---

## 1. PRD – Product Requirements Document

### 1.1 Visão Geral

O EcoFuel é um aplicativo móvel para motoristas que desejam reduzir gastos com combustível. O sistema oferece análise inteligente de consumo, comparação de preços de postos, rotas econômicas e um agente de IA chamado EcoBot.

### 1.2 Problema

Motoristas perdem dinheiro por:

* Abastecer em postos mais caros.
* Tráfego e rotas ineficientes.
* Falta de controle de consumo.
* Falta de orientação personalizada.

### 1.3 Solução

* Comparação instantânea de preços.
* Rotas otimizadas para menor gasto.
* Relatórios mensais.
* Assistente EcoBot com dicas personalizadas.
* Registro fácil de abastecimentos.

### 1.4 Público-alvo

* Motoristas urbanos.
* Motoristas de app.
* Pequenos frotistas.

### 1.5 MVP – Funcionalidades obrigatórias

* Login/Cadastro.
* Registrar abastecimento.
* Dashboard com resumo mensal.
* Comparar preços de postos.
* Rotas econômicas.
* Chat básico EcoBot.

### 1.6 Requisitos de sucesso

* Economia percebida.
* Boa usabilidade.
* 95%+ de estabilidade.

---

## 2. Persona do Agente EcoBot

### Nome: **EcoBot – Seu Consultor de Economia de Combustível**

* Tom: amigável, direto e motivador.
* Personalidade: educativo, paciente, orientador.
* Evita: termos técnicos complicados.
* Chama o usuário: “Motorista”, “Amigo de estrada”.

### Exemplos:

* “Percebi que sua média de consumo piorou esta semana. Quer ajuda com rotas melhores?”
* “Boa escolha! Este posto está 8% mais barato que sua média.”

---

## 3. Jornada do Usuário

### Etapas

1. **Descoberta** → vê anúncio/indicação.
2. **Instalação** → baixa o app.
3. **Cadastro** → entra com e-mail.
4. **Primeiro uso** → EcoBot guia o usuário.
5. **Registro de abastecimento**.
6. **Rotas econômicas**.
7. **Relatório mensal**.
8. **Economia percebida**.

### Emoções

* Curiosidade.
* Satisfação ao economizar.
* Confiança no EcoBot.

### Oportunidades

* Gamificação.
* Alertas inteligentes.

---

## 4. Fluxo de Navegação

### Diagrama

```
Login → Dashboard → (Chat EcoBot | Registrar Abastecimento | Rotas Econômicas | Comparar Postos | Relatório Mensal | Configurações)
```

### Explicação

* **Login** → autentica.
* **Dashboard** → visão geral.
* **EcoBot** → orienta.
* **Rotas** → algoritmos de economia.
* **Postos** → lista com preço.
* **Relatórios** → análise mensal.

---

## 5. Wireframes (ASCII)

### 5.1 Login

```
+----------------------------------+
|         ECOFUEL LOGIN            |
|  Email: [__________]             |
|  Senha: [__________]             |
|  [ Entrar ]                      |
|  Criar conta                     |
+----------------------------------+
```

### 5.2 Dashboard

```
+---------------- Dashboard ----------------+
| Consumo mês:  R$ 412                     |
| KM rodados:   723 km                     |
| Economia:     11%                        |
|------------------------------------------|
| [ Registrar Abastecimento ]              |
| [ Rotas Econômicas ]                     |
| [ Comparar Postos ]                      |
| [ Relatório Mensal ]                     |
| [ Falar com EcoBot ]                     |
+------------------------------------------+
```

### 5.3 Comparação de Postos

```
+-------------- Postos Próximos -----------+
| Posto A      R$ 5,29 / L                 |
| Posto B      R$ 5,18 / L  (melhor)       |
| Posto C      R$ 5,34 / L                 |
+------------------------------------------+
```

### 5.4 Rotas Econômicas

```
+-------------- Rota Econômica ------------+
| Origem: [____]                           |
| Destino: [____]                          |
| [ Calcular ]                             |
|------------------------------------------|
| Economia estimada: R$ 3,21              |
| Distância: 8,2 km                        |
+------------------------------------------+
```

---

## 6. Arquitetura Técnica

### Backend

* **Node.js + NestJS** (recomendado)
* Autenticação JWT
* Serviços:

  * Preços de combustível
  * Rotas econômicas
  * Registro de abastecimento
  * IA EcoBot (API LLM)

### Banco de Dados

* PostgreSQL

### Infraestrutura

* AWS

  * RDS
  * Lambda para cálculo de rotas
  * S3 para relatórios

### IA

* API de LLM (OpenAI, Groq ou Gemini)
* RAG opcional para personalização

---

## 7. Modelo de Banco de Dados

### Tabelas

#### **users**

* id (PK)
* nome
* email
* senha_hash

#### **fuel_logs**

* id (PK)
* user_id (FK)
* litros
* preco_litro
* total
* data_abastecimento

#### **stations**

* id
* nome
* latitude
* longitude
* preco_atual

#### **routes_history**

* id
* user_id
* origem
* destino
* economia_estim
* km

#### ER Diagram (texto)

```
users 1---N fuel_logs
users 1---N routes_history
stations independent
```

---

## 8. API – Rotas

### Autenticação

```
POST /auth/login
POST /auth/register
```

### Abastecimentos

```
POST /fuel
GET /fuel/monthly
```

### Postos

```
GET /stations/nearby?lat=x&lng=y
```

### Rotas

```
POST /routes/calc
```

### EcoBot

```
POST /ecobot/chat
```

---

## 9. Plano de Validação

### Hipóteses

* Usuários não sabem onde economizar.
* Rotas otimizadas reduzem 4–8% do consumo.

### Testes

* Entrevistas com motoristas.
* Prototipagem.
* Coleta de percepção de economia.

### Métricas

* % economia percebida.
* Uso diário.
* Interações com EcoBot.

---

## 10. Plano de Testes (QA)

* Testes de login.
* Cálculo de consumo.
* Cálculo de rotas.
* UX / fluxo geral.
* APIs e estresse.

---

## 11. README.md (versão final incorporada)

# EcoFuel – Economia Inteligente de Combustível

Aplicativo focado em redução de gastos através de rotas eficientes, análise de abastecimentos e um agente de IA.

## Funcionalidades

* Registro de abastecimento
* IA EcoBot
* Comparação de postos
* Rotas econômicas
* Relatório mensal

## MVP

* Autenticação
* Dashboard
* Rotas
* Registro de consumo

## Tecnologias

* Node.js + NestJS
* PostgreSQL
* AWS
* API LLM

## Evolução

* Gamificação
* Histórico avançado
* Previsões de gasto

## Reflexão Final

Projeto aplicável ao mercado, útil e escalável.

Projeto educacional — livre para estudo e evolução.
