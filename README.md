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

## 3. Estrutura do repositório

```text
mhealth-diabetes/
│
├── README.md
├── .gitignore
├── .env.example
│
├── app/
│   ├── index.html
│   ├── package.json
│   ├── package-lock.json
│   ├── public/
│   └── src/
│       ├── components/
│       ├── pages/
│       ├── services/
│       ├── hooks/
│       ├── contexts/
│       ├── assets/
│       ├── styles/
│       └── utils/
│
├── api/
│   ├── manage.py
│   ├── requirements.txt
│   │
│   ├── config/
│   │   ├── settings.py
│   │   ├── urls.py
│   │   ├── asgi.py
│   │   └── wsgi.py
│   │
│   └── apps/
│       ├── accounts/
│       ├── patients/
│       ├── assessments/
│       ├── decision_support/
│       └── audit/
│
├── database/
│   ├── scripts/
│   ├── seeds/
│   ├── imports/
│   ├── schemas/
│   └── diagrams/
│
├── docs/
│   ├── architecture/
│   ├── requirements/
│   ├── clinical/
│   ├── api/
│   ├── security/
│   ├── ui/
│   ├── user-manual/
│   └── technical-manual/
│
└── tests/
    ├── integration/
    ├── e2e/
    ├── clinical/
    ├── security/
    └── fixtures/
```

---

## 4. Diretório `/app`

Contém o frontend desenvolvido em React.

Responsável por:

- interface do usuário;
- login;
- dashboard;
- formulários;
- cadastro e consulta;
- avaliação de Diabetes Mellitus;
- apresentação das recomendações;
- responsividade;
- experiência de utilização em smartphones;
- comunicação com a API Django.

O ponto de entrada HTML do frontend encontra-se em:

```text
/app/index.html
```

A estrutura exata poderá variar conforme a ferramenta adotada para construção do React.

---

## 5. Diretório `/api`

Contém o backend desenvolvido com Django e Django REST Framework.

Responsável por:

- autenticação;
- autorização;
- usuários;
- pacientes/casos;
- avaliações;
- regras de negócio;
- processamento das informações;
- apoio à decisão;
- comunicação com PostgreSQL;
- auditoria;
- APIs REST;
- segurança da aplicação.

O Django deve ser dividido em aplicações menores segundo as responsabilidades do domínio.

Exemplo:

```text
api/apps/

accounts/          → usuários e autenticação
patients/          → pacientes/casos
assessments/       → avaliações de enfermagem
decision_support/  → motor de apoio à decisão
audit/             → auditoria
```

---

## 6. Diretório `/database`

Contém recursos auxiliares relacionados ao banco PostgreSQL.

Exemplos:

```text
database/
├── scripts/
├── seeds/
├── imports/
├── schemas/
└── diagrams/
```

Este diretório **não deve armazenar o banco de dados PostgreSQL propriamente dito**.

As migrations criadas pelo Django devem permanecer dentro das respectivas aplicações Django e devem ser versionadas no Git.

Exemplo:

```text
api/apps/patients/migrations/
api/apps/assessments/migrations/
```

Não adicionar arquivos físicos do PostgreSQL ao GitHub.

---

## 7. Diretório `/docs`

Contém a documentação técnica e funcional do projeto.

Pode incluir:

- arquitetura;
- requisitos funcionais;
- requisitos não funcionais;
- diagramas;
- fluxos;
- documentação das APIs;
- documentação de segurança;
- documentação das regras clínicas;
- referências;
- manual do usuário;
- manual técnico;
- decisões arquiteturais.

Para o motor de apoio à decisão, deve ser mantida rastreabilidade entre:

```text
Fonte científica
        ↓
Regra clínica
        ↓
Implementação
        ↓
Teste
        ↓
Recomendação
```

---

## 8. Diretório `/tests`

Destinado principalmente aos testes que atravessam diferentes componentes da aplicação.

Exemplos:

- integração frontend/backend;
- testes end-to-end;
- testes clínicos;
- testes de segurança;
- fixtures;
- cenários simulados.

Testes unitários específicos do Django podem permanecer próximos às aplicações correspondentes.

---

# Configuração do ambiente de desenvolvimento

## 9. Pré-requisitos

Cada desenvolvedor deverá instalar localmente:

- Git
- Visual Studio Code
- Python
- Node.js
- npm
- PostgreSQL

Os desenvolvedores podem utilizar Windows 11 ou Ubuntu 24.04 LTS.

Não é necessário que os caminhos de instalação sejam iguais entre os computadores.

---

# Backend — Django

## 10. Criar ambiente virtual Python

O ambiente virtual é individual e **não deve ser enviado ao GitHub**.

### Windows 11

A partir do diretório `/api`:

```bash
python -m venv .venv
```

Ativação no PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

### Ubuntu 24.04 LTS

```bash
python3 -m venv .venv
```

Ativação:

```bash
source .venv/bin/activate
```

Após ativado, instalar as dependências:

```bash
pip install -r requirements.txt
```

---

## 11. Dependências Python

As dependências compartilhadas devem ser registradas em:

```text
api/requirements.txt
```

Exemplo:

```text
Django
djangorestframework
psycopg
django-cors-headers
python-dotenv
```

Não compartilhar a pasta `.venv`.

Compartilhar apenas o arquivo de dependências.

Quando uma dependência necessária ao projeto for adicionada, o arquivo de dependências deverá ser atualizado.

---

# Frontend — React

## 12. Instalação

Entrar no diretório:

```bash
cd app
```

Instalar dependências:

```bash
npm install
```

O npm reconstruirá localmente:

```text
node_modules/
```

Portanto, `node_modules` **nunca deve ser enviado ao GitHub**.

Os arquivos:

```text
package.json
package-lock.json
```

devem ser versionados.

Isso permite que todos os integrantes instalem versões consistentes das dependências.

---

# PostgreSQL

## 13. Banco de dados local

Cada desenvolvedor poderá possuir seu próprio PostgreSQL local.

Exemplo:

```text
Desenvolvedor A
PostgreSQL local
Banco: mhealth_dev

Desenvolvedor B
PostgreSQL local
Banco: mhealth_dev
```

Usuários, senhas, portas e caminhos podem ser diferentes.

Essas diferenças **não devem ser colocadas diretamente no código-fonte**.

---

# Variáveis de ambiente

## 14. `.env`

Informações específicas da máquina ou informações secretas devem ser armazenadas em variáveis de ambiente.

Exemplo de `.env` local:

```text
DEBUG=True

DB_NAME=mhealth_dev
DB_USER=postgres
DB_PASSWORD=senha_local
DB_HOST=localhost
DB_PORT=5432

DJANGO_SECRET_KEY=chave-local

FRONTEND_URL=http://localhost:5173
```

O arquivo:

```text
.env
```

**NUNCA deve ser enviado ao GitHub.**

---

## 15. `.env.example`

O repositório deverá possuir:

```text
.env.example
```

Exemplo:

```text
DEBUG=

DB_NAME=
DB_USER=
DB_PASSWORD=
DB_HOST=
DB_PORT=

DJANGO_SECRET_KEY=

FRONTEND_URL=
```

Cada desenvolvedor copia esse arquivo e cria seu próprio `.env`.

Nunca inserir credenciais reais no `.env.example`.

---

# Execução

## 16. Backend Django

Com ambiente virtual ativado:

```bash
cd api
python manage.py migrate
python manage.py runserver
```

No Ubuntu, dependendo da configuração:

```bash
python3 manage.py runserver
```

Por padrão:

```text
http://127.0.0.1:8000/
```

---

## 17. Frontend React

Em outro terminal:

```bash
cd app
npm install
npm run dev
```

O endereço local dependerá da ferramenta de build utilizada.

Em uma configuração Vite típica:

```text
http://localhost:5173/
```

---

# Git e GitHub

## 18. Regra fundamental

O GitHub deve conter aquilo que é necessário para **reproduzir o projeto**, e não o ambiente pessoal de cada desenvolvedor.

Deve ser versionado:

```text
Código-fonte
Configurações compartilhadas
package.json
package-lock.json
requirements.txt
migrations Django
testes
documentação
scripts
```

Não deve ser versionado:

```text
.venv
venv
node_modules
.env
senhas
credenciais
banco local
logs
cache
build local
configurações pessoais do VS Code
arquivos temporários
arquivos específicos do Windows
arquivos específicos do Linux
```

---

## 19. Fluxo Git

Fluxo sugerido:

```text
main
  │
  └── develop
        │
        ├── feature/login
        ├── feature/dashboard
        ├── feature/patients
        ├── feature/assessment
        └── feature/decision-support
```

Processo:

```text
Issue
  ↓
Feature branch
  ↓
Desenvolvimento
  ↓
Testes
  ↓
Pull Request
  ↓
Code Review
  ↓
Validação
  ↓
Merge
```

Não realizar alterações diretamente em `main`.

---

## 20. Pull Requests

Cada Pull Request deverá informar:

- funcionalidade desenvolvida;
- Issue relacionada;
- arquivos/componentes afetados;
- testes realizados;
- alterações no banco;
- novas dependências;
- eventuais impactos em frontend/backend;
- screenshots quando houver alteração visual.

O responsável técnico deverá revisar os Pull Requests antes do merge nas branches protegidas.

---

# Segurança

## 21. Nunca enviar ao GitHub

Não versionar:

- senhas PostgreSQL;
- `DJANGO_SECRET_KEY`;
- tokens;
- chaves de API;
- certificados privados;
- credenciais de hospedagem;
- dados reais de pacientes;
- arquivos `.env`;
- backups reais do banco.

Caso uma credencial seja acidentalmente publicada, removê-la do repositório **não é suficiente**. A credencial deverá ser considerada comprometida e substituída.

---

# Ambientes

O projeto deverá distinguir:

```text
DESENVOLVIMENTO
       ↓
HOMOLOGAÇÃO
       ↓
PRODUÇÃO
```

Configurações específicas de cada ambiente não deverão ser codificadas diretamente no código-fonte.

---

# Objetivo de portabilidade

Um desenvolvedor utilizando Windows 11 deverá conseguir clonar o mesmo repositório utilizado por outro desenvolvedor em Ubuntu 24.04 LTS e reconstruir seu ambiente a partir dos arquivos versionados.

A regra é:

> **Versionar o projeto; não versionar a máquina do desenvolvedor.**

---

## Equipe

O desenvolvimento é realizado de forma colaborativa por professor e alunos da área de tecnologia, utilizando GitHub para versionamento, revisão de código, Pull Requests, Issues e documentação da evolução do protótipo.

---

## Status

Protótipo em desenvolvimento para finalidade acadêmica e de pesquisa.

Não destinado, nesta etapa, à utilização autônoma como sistema assistencial em produção.
