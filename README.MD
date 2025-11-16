# 📋 Sistema de Controle de Ponto e Gestão de Remetentes - APAC

> **Projeto Final do Curso Técnico em Informática**  
> IFES Campus Cachoeiro de Itapemirim - ES

---

## 🎓 Informações do Projeto

| Informação| Detalhes |
|-----------|----------|
| **Instituição** | IFES - Instituto Federal do Espírito Santo |
| **Campus** | Cachoeiro de Itapemirim - ES |
| **Curso** | Técnico em Informática |
| **Professor** | Ricardo Maroquio - Programação |
| **Tipo de Projeto** | Trabalho Final / Capstone |
| **Objetivo** | Conclusão do Curso Técnico com Aplicação Full-Stack |
| **Público-Alvo** | APAC-Feminino e Instituições Penitenciárias |
| **Data de Desenvolvimento** | 2025 |

---

## 📖 Sobre o Projeto

Este é um **Sistema Web Completo de Controle de Ponto e Gestão de Remetentes** desenvolvido como projeto final do curso técnico em informática do IFES Campus de Cachoeiro de Itapemirim - ES, sob orientação do professor **Ricardo Maroquio**, especialista em programação.

O projeto aplica conceitos de **desenvolvimento full-stack** na prática, integrando tecnologias frontend e backend para criar uma solução completa de gestão penitenciária.

Durante o desenvolvimento, aplicamos todos os conhecimentos adquiridos em aulas de programação, especialmente em desenvolvimento web, banco de dados e boas práticas de engenharia de software.

---

## 🎯 Objetivos Educacionais

- ✅ Aplicar conhecimentos de desenvolvimento full-stack
- ✅ Integrar banco de dados relacional com API REST
- ✅ Implementar autenticação de usuários
- ✅ Gerar relatórios em PDF
- ✅ Criar interface responsiva e intuitiva
- ✅ Praticar boas práticas de engenharia de software
- ✅ Desenvolver solução para problema real (gestão penitenciária)

---

## 🏗️ Arquitetura do Projeto

### **Stack Tecnológico**

```
┌─────────────────────────────────────────┐
│         CAMADA DE APRESENTAÇÃO          │
│  HTML5 | CSS3 | JavaScript | Bootstrap  │
└──────────────────┬──────────────────────┘
                   │
┌──────────────────▼──────────────────────┐
│    CAMADA DE LÓGICA DE NEGÓCIO          │
│  FastAPI | Python | Jinja2 Templates    │
└──────────────────┬──────────────────────┘
                   │
┌──────────────────▼──────────────────────┐
│    CAMADA DE DADOS E PERSISTÊNCIA       │
│  SQLite | SQLAlchemy | SQL Scripts      │
└─────────────────────────────────────────┘
```

### **Dependências Principais**

```txt
fastapi[standard]      # Framework web moderno e rápido
uvicorn[standard]      # Servidor ASGI para Python
jinja2                 # Motor de templates HTML
```

---

## 📁 Estrutura de Diretórios

```
Sistema-Carcerario-8/
├── 📄 main.py                          # Aplicação principal FastAPI
├── 📄 calculo_horas.py                 # Lógica de cálculo de dias remidos
├── 📄 pdf.py                           # Geração de relatórios PDF
├── 📄 requirements.txt                 # Dependências do projeto
│
├── 📁 models/                          # Camada de modelos de dados
│   ├── base.py                         # Modelo SQLAlchemy - Usuário
│   ├── conectar_sql.py                 # Configuração de conexão BD
│   ├── encarregado.py                  # Dataclass do Encarregado
│   ├── registro_ponto.py               # Dataclass do Registro de Ponto
│   ├── remetente.py                    # Dataclass do Remetente
│   └── get_db.py                       # Dependency injection do BD
│
├── 📁 repo/                            # Camada de repositório (DAO)
│   ├── encarregado_repo.py             # Operações com Encarregados
│   ├── registro_ponto_repo.py          # Operações com Registros de Ponto
│   └── remetente_repo.py               # Operações com Remetentes
│
├── 📁 sql/                             # Scripts SQL
│   ├── encarregado_sql.py              # Queries do Encarregado
│   ├── registro_ponto_sql.py           # Queries de Registro de Ponto
│   └── remetente_sql.py                # Queries de Remetente
│
├── 📁 data/                            # Camada de acesso a dados
│   ├── database.py                     # Conexão SQLite
│   └── inserts_encarregado.sql         # Dados iniciais
│
├── 📁 templates/                       # Páginas HTML (Jinja2)
│   ├── login.html                      # Tela de autenticação
│   ├── inicial.html                    # Dashboard inicial
│   ├── ponto.html                      # Batimento de ponto
│   ├── cadastro.html                   # Cadastro de remetentes
│   ├── consulta.html                   # Consulta e edição de dados
│   └── relatorio.html                  # Geração de relatórios
│
├── 📁 static/                          # Arquivos estáticos
│   ├── apac.png                        # Logo/Imagem APAC
│   └── pdfs/                           # Relatórios gerados
│
└── 📁 .vscode/                         # Configurações do VS Code
    ├── launch.json                     # Configuração de debug
    └── settings.json                   # Configurações do projeto
```

---

## 🔑 Funcionalidades Principais

### **1. Autenticação de Usuários** 
**Localização:** `main.py` - Rotas `/` e `/formlogin`

- ✅ Login com validação de credenciais
- ✅ Verificação em banco de dados
- ✅ Redirecionamento condicional
- ✅ Sessões seguras

**Usuários de Teste:**
| Usuário | Senha |
|---------|-------|
| luizeduardo | 123456 |
| igorgomes | 654321 |

### **2. Controle de Ponto** ⏰
**Localização:** `templates/ponto.html` | `main.py` - Rota `/ponto`

Funcionalidades:
- ✅ Registrar entrada/saída
- ✅ Intervalo de almoço
- ✅ Validação de sequência correta
- ✅ Cálculo automático de dias remidos
- ✅ Visualização em tabela interativa

**Lógica de Cálculo:** `calculo_horas.py`

Formula para dias remidos:
```
Dias Remidos = [(entrada_intervalo - entrada) + (saída - saída_intervalo)] / 8 horas
```

### **3. Gestão de Remetentes** 👥
**Localização:** `templates/cadastro.html` | `templates/consulta.html`

Operações CRUD completas:
- ✅ **Criar:** Cadastro de novos remetentes (Rota: `/formcadastro`)
- ✅ **Ler:** Listagem e consulta (Rota: `/consulta`)
- ✅ **Atualizar:** Edição inline (Rota: `/atualizar`)
- ✅ **Deletar:** Exclusão por ID (Rota: `/excluir`)

**Campos armazenados:**
- Nome do remetente
- Data de nascimento
- Artigo penal
- Tempo de sentença
- Número da cela
- Comportamento

### **4. Geração de Relatórios PDF** 📄
**Localização:** `pdf.py` | `templates/relatorio.html`

Funcionalidades:
- ✅ Conversão de registros de ponto em PDF
- ✅ Armazenamento em `static/pdfs/`
- ✅ Download direto via navegador
- ✅ Limpeza de relatórios antigos

---

## 📊 Modelos de Dados

### **Remetente** (models/remetente.py)
```python
@dataclass
class Remetente:
    id: int
    remetente: str
    data_nascimento: date
    artigo: int
    tempo_sentenca: str
    cela: str
    comportamento: str
```

### **Registro de Ponto** (models/registro_ponto.py)
```python
@dataclass
class RegistroPonto:
    id: int
    data: date
    remetente: str
    entrada: time
    entrada_intervalo: time
    saida_intervalo: time
    saida: time
    dias_remidos: float
```

### **Encarregado** (models/encarregado.py)
```python
@dataclass
class Encarregado:
    id: int
    usuario: str
    senha: str
```

---

## 🗄️ Banco de Dados

**Sistema:** SQLite (`dados.db`)

### **Tabelas**

#### **Tabela: Remetentes**
```sql
CREATE TABLE Remetentes (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    remetente TEXT NOT NULL,
    data_nascimento DATE NOT NULL,
    crime TEXT NOT NULL,
    tempo_sentenca TEXT NOT NULL,
    cela TEXT NOT NULL,
    comportamento TEXT NOT NULL
);
```

#### **Tabela: registro_ponto**
```sql
CREATE TABLE registro_ponto (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    data DATE NOT NULL,
    remetente TEXT NOT NULL,
    entrada TIME NOT NULL,
    entrada_intervalo TIME NOT NULL,
    saida_intervalo TIME NOT NULL,
    saida TIME NOT NULL,
    dias_remidos REAL NOT NULL
);
```

#### **Tabela: Encarregado**
```sql
CREATE TABLE Encarregado (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    usuario TEXT NOT NULL,
    senha TEXT NOT NULL
);
```

---

## 🌐 Rotas da API

| Método | Rota | Descrição |
|--------|------|-----------|
| GET | `/` | Página de login |
| POST | `/formlogin` | Autenticação de usuário |
| GET | `/inicial` | Dashboard inicial |
| GET | `/ponto` | Tela de controle de ponto |
| POST | `/salvar_todos` | Salvar registros de ponto |
| POST | `/salvarpdf` | Gerar PDF de relatórios |
| GET | `/cadastro` | Formulário de cadastro de remetente |
| POST | `/formcadastro` | Salvar novo remetente |
| GET | `/relatorio` | Listar relatórios PDF gerados |
| POST | `/limpar_pdfs` | Deletar relatórios PDF |
| GET | `/consulta` | Listar todos os remetentes |
| POST | `/atualizar` | Atualizar dados do remetente |
| POST | `/excluir` | Deletar remetente |

---

## 🎨 Interface do Usuário

### **Design Responsivo**
- Bootstrap 5.3.6
- CSS customizado
- Navbar fixa com menu hamburguer
- Sidebar colapsível
- Tabelas responsivas
- Compatível com desktop e mobile

### **Funcionalidades JavaScript**
- Validação de formulários
- Toggle sidebar
- Edição inline de tabelas
- Formatação de dados JSON
- Geração dinâmica de PDFs

---

## 🔒 Segurança

⚠️ **Notas de Segurança Importantes:**

- Usar hash bcrypt para senhas em produção
- Implementar HTTPS/TLS
- Adicionar CORS (Cross-Origin Resource Sharing)
- Validação e sanitização de inputs
- Rate limiting na API
- Implementar tokens JWT
- Adicionar autenticação multi-fator

---

## 🚀 Como Executar

### **Pré-requisitos**
- Python 3.8 ou superior
- pip (gerenciador de pacotes Python)
- Git (opcional)

### **Instalação**

```bash
# 1. Clonar ou extrair o projeto
cd Sistema-Carcerario-8

# 2. Criar ambiente virtual (recomendado)
python -m venv venv

# 3. Ativar ambiente virtual
# Windows
venv\Scripts\activate

# Linux/Mac
source venv/bin/activate

# 4. Instalar dependências
pip install -r requirements.txt
```

### **Execução**

```bash
# Iniciar servidor de desenvolvimento
python main.py

# Ou manualmente com uvicorn
uvicorn main:app --reload --host 127.0.0.1 --port 8000
```

**Acesso:** `http://127.0.0.1:8000`

### **Parar o Servidor**
```
Pressione Ctrl + C no terminal
```

---

## 📝 Guia de Uso

### **1. Fazer Login**
- Acesse `http://127.0.0.1:8000`
- Use credenciais de teste (ver tabela acima)
- Clique em "Entrar"

### **2. Batimento de Ponto**
- Acesse "Ponto" no menu
- Selecione o remetente
- Registre: Entrada → Saída Intervalo → Entrada Intervalo → Saída
- Os dias remidos serão calculados automaticamente
- Clique em "Salvar" para persistir dados

### **3. Cadastrar Remetente**
- Acesse "Cadastro" no menu
- Preencha todos os campos
- Clique em "Cadastrar"

### **4. Consultar/Editar Remetentes**
- Acesse "Consulta" no menu
- Edite os dados inline
- Clique em "Excluir" para remover

### **5. Gerar Relatório PDF**
- Acesse "Relatório" no menu
- Clique em "Gerar PDF"
- Download será iniciado automaticamente

---

## 💼 Potencial Comercial

Este sistema foi desenvolvido com o objetivo de oferecer uma solução robusta para a **APAC-Feminino** e outras instituições penitenciárias.

### **Benefícios para APAC e Instituições Penitenciárias:**

✅ Automação do controle de ponto  
✅ Rastreamento automático de dias remidos  
✅ Relatórios gerados em PDF  
✅ Redução de paperwork  
✅ Interface intuitiva e de fácil uso  
✅ Escalabilidade para múltiplas unidades  
✅ Redução de erros de registro manual  
✅ Conformidade com legislação penitenciária  

### **Oportunidades de Monetização:**

- 💰 Venda de licenças por instituição
- 💰 Suporte e manutenção contínua
- 💰 Customizações específicas conforme necessidade
- 💰 Treinamento de operadores
- 💰 Hosting em nuvem
- 💰 Módulos adicionais (biometria, segurança, integração com sistemas externos)
- 💰 Consultoria em processo de implementação

---

## 📚 Tecnologias Utilizadas

| Camada | Tecnologia |
|--------|-----------|
| **Frontend** | HTML5, CSS3, JavaScript, Bootstrap 5.3.6 |
| **Backend** | Python 3, FastAPI, Jinja2 |
| **Database** | SQLite, SQLAlchemy |
| **Server** | Uvicorn (ASGI) |
| **IDE** | Visual Studio Code |

---

## 🤝 Contribuidores

- **Desenvolvimento:** Luiz Eduardo Lima Balbino,Gabriel Biancardi e Igor Gomes Menegazzi
- **Orientação:** Prof. Ricardo Maroquio
- **Instituição:** IFES Campus Cachoeiro de Itapemirim - ES

---

## 📄 Licença

Este projeto foi desenvolvido para fins educacionais e comerciais. 

Para mais informações sobre licença e uso comercial, entre em contato com a instituição.

---

## 📞 Contato e Suporte

Para dúvidas, sugestões ou interesse em implementação:

- **Professor:** Ricardo Maroquio
- **Instituição:** IFES Campus Cachoeiro de Itapemirim
- **Estado:** Espírito Santo, Brasil

---

## 🔄 Versão

**Versão:** 1.0.0  
**Data:** Novembro de 2025  
**Status:** Projeto Final - Concluído

---

## ✨ Conclusão

Este projeto demonstra a aplicação prática de conceitos de engenharia de software e desenvolvimento full-stack no contexto real de gestão penitenciária, culminando em uma solução funcional, escalável e pronta para implementação em ambientes corporativos.

**Desenvolvido como ferramenta educacional e profissional para o contexto do sistema penitenciário brasileiro, especialmente para a APAC-Feminino.**

---

*Projeto Final - Curso Técnico em Informática - IFES Campus Cachoeiro de Itapemirim - ES* 🎓