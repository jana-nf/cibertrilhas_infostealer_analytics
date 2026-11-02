# 🛡️ CiberTrilhas Analytics

Pipeline de Engenharia e Análise de Dados de ponta a ponta para simulação, correlação e monitorização de ataques em cadeia (Multi-Stage Attacks) em cibersegurança.

---

## 🌐 Sobre o Projeto

O **CiberTrilhas Analytics** resolve um dos maiores desafios das equipas de segurança modernas: a **visibilidade fragmentada**. O cibercrime atual opera em cadeia:
1. **Infostealer / MaaS:** Credenciais corporativas são roubadas de dispositivos comprometidos e comercializadas[cite: 1].
2. **Acesso Corporativo:** Atacantes ("afiliados") utilizam essas credenciais para entrar na rede da empresa através de IPs externos.
3. **Exploração de Aplicação:** Com acesso interno, realizam varreduras e tentativas de exploração de falhas, como **SQL Injection (SQLi)**[cite: 1].

Este projeto une **Engenharia de Dados** e **Cibersegurança** para cruzar estes eventos que, isoladamente, pareceriam ruído, transformando-os numa linha do tempo unificada de incidentes.

---

## 🏗️ Arquitetura e Persistência Poliglota

O pipeline utiliza uma arquitetura híbrida de bases de dados:
* **MongoDB (NoSQL):** Armazena dados semi-estruturados e flexíveis de inteligência de ameaças (*stealer logs* e metadados de malwares).
* **PostgreSQL (Relacional):** Armazena os registos relacionais estruturados de autenticação corporativa e logs de WAF/aplicação (`corporate_auth_logs` e `app_sqli_logs`).
* **Motor de Correlação:** Cruza temporalmente o momento do vazamento da credencial, o login suspeito e a respetiva tentativa de SQLi.
* **Streamlit & Telegram:** Interface de visualização analítica e bot de envio de alertas automatizados em tempo real.

---

## 📂 Estrutura do Repositório

```text
ciberrilhas-analytics/
│
├── generate_synthetic_data.py   # Gerador de dados sintéticos para simulação
├── etl_pipeline.py              # Pipeline ETL (Ingestão MongoDB + PostgreSQL)
├── app_dashboard.py             # Dashboard interativo de investigação (Streamlit)
├── telegram_alerter.py          # Módulo de alertas automáticos em tempo real
└── requirements.txt             # Dependências do projeto
```

## 📊 Demonstração do Dashboard
O painel construído em Streamlit exibe:

Métricas consolidadas (KPIs) de ameaças detetadas.

Tabela dinâmica com a correlação exata do incidente em cadeia.

Gráficos analíticos dos payloads de SQLi mais frequentes.


## 🛠️ Tecnologias Utilizadas
Python (Pandas, NumPy, Faker)

MongoDB & PyMongo

PostgreSQL & Psycopg2

Streamlit

Telegram Bot API


