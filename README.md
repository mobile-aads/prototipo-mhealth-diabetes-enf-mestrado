# Protótipo Sistema Web mHealth DiabEnf — Diabetes Mellitus

Protótipo funcional de sistema Web destinado ao apoio à tomada de decisão do profissional enfermeiro no atendimento e acompanhamento de pessoas com **Diabetes Mellitus (DM)** no contexto da Atenção Primária à Saúde.

O projeto integra um trabalho acadêmico de mestrado e utiliza conceitos relacionados à **Mobile Health (mHealth)**. A aplicação será responsiva, permitindo utilização em computadores desktop, notebooks e smartphones.

> **Importante:** o protótipo constitui uma ferramenta de apoio à tomada de decisão e não substitui a avaliação clínica, o julgamento profissional do enfermeiro ou os protocolos e normas aplicáveis à assistência em saúde.

---

## 1. Tecnologias

### Frontend

- React
- JavaScript/TypeScript, conforme definição da equipe
- HTML5
- CSS3
- Node.js
- npm

### Backend

- Python 3
- Django
- Django REST Framework — DRF

### Banco de dados

- PostgreSQL

### Desenvolvimento e versionamento

- Visual Studio Code
- Git
- GitHub

### Sistemas operacionais suportados no desenvolvimento

- Windows 11
- Ubuntu 24.04 LTS

O projeto deve permanecer independente do sistema operacional utilizado pelo desenvolvedor. Arquivos específicos de ambientes locais não devem ser adicionados ao repositório.

---

## 2. Arquitetura geral

A aplicação utiliza uma arquitetura separando frontend, backend e persistência de dados:

```text
┌──────────────────────────────┐
│          USUÁRIO             │
│        Enfermeiro(a)         │
└──────────────┬───────────────┘
               │
               │ HTTPS
               ▼
┌──────────────────────────────┐
│           REACT              │
│          Frontend            │
│            /app              │
└──────────────┬───────────────┘
               │
               │ REST API / JSON
               ▼
┌──────────────────────────────┐
│          DJANGO              │
│  Django REST Framework       │
│           /api               │
└──────────────┬───────────────┘
               │
               │ ORM
               ▼
┌──────────────────────────────┐
│        POSTGRESQL            │
│       Banco de Dados         │
└──────────────────────────────┘
```

---
