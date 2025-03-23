
# **Jornada de Dados - Bootcamp de Python - Aula 16**

## **Descrição do Projeto**

Este repositório contém os materiais e códigos utilizados na **Aula 16 do Bootcamp de Python**, parte da **Jornada de Dados**. O foco da aula é o aprendizado de **SQLModel** e a revisão de conceitos essenciais de **SQLAlchemy**, com ênfase na interação entre Python e bancos de dados relacionais.

## **Conteúdo da Aula**

Na **Aula 16**, exploramos os seguintes tópicos:

1. **Introdução ao SQLModel**
   - SQLModel é uma biblioteca que facilita o uso do **SQLAlchemy** com uma interface simples e moderna. Ela combina a simplicidade do SQLAlchemy com a clareza das anotações de tipos do Python.
   - Utilizamos SQLModel para criar e manipular modelos de banco de dados de maneira eficiente, integrando com bancos como SQLite, PostgreSQL e MySQL.

2. **Conceitos do SQLAlchemy**
   - **SQLAlchemy** é uma biblioteca poderosa de mapeamento objeto-relacional (ORM) em Python. Durante a aula, revisamos:
     - **Engines e Conexões**: como conectar Python a um banco de dados.
     - **Sessões**: como usar a sessão para interagir com o banco de dados de forma eficiente.
     - **Consultas**: como realizar queries utilizando o SQLAlchemy.
     - **Modelagem**: criação de classes de modelos para tabelas no banco de dados.

3. **Integração de SQLModel com SQLAlchemy**
   - Vimos como usar SQLModel para criar modelos de dados que são diretamente integrados ao SQLAlchemy, facilitando a definição de tabelas e a execução de operações CRUD.

## **Tecnologias Utilizadas**

- **Python**: Linguagem principal do projeto.
- **SQLModel**: Biblioteca para simplificar a interação com bancos de dados relacionais.
- **SQLAlchemy**: ORM (Object Relational Mapper) para bancos de dados.
- **SQLite** (ou outro banco de dados conforme o projeto): Banco de dados utilizado durante a aula para demonstração.

## **Como Executar**

1. **Clonar o repositório**

   Primeiro, clone o repositório para o seu ambiente local:

   ```bash
   git clone https://link-para-o-repositorio.git
   cd nome-do-repositorio
   ```

2. **Instalar dependências**

   Utilize o **Poetry** ou o **pip** para instalar as dependências necessárias.

   - Usando Poetry:

     ```bash
     poetry install
     ```

   - Usando pip:

     Crie um ambiente virtual e instale as dependências:

     ```bash
     python -m venv .venv
     .venv\Scripts ctivate  # No Windows
     source .venv/bin/activate  # No Linux/Mac
     pip install -r requirements.txt
     ```

3. **Executar o Projeto**

   Após instalar as dependências, execute os scripts ou interaja com o banco de dados conforme necessário. Para um exemplo de execução de scripts:

   ```bash
   python exemplo_script.py
   ```

## **Estrutura de Diretórios**

```
├── .venv/                  # Ambiente virtual (se aplicável)
├── README.md               # Este arquivo
├── exemplo_script.py       # Exemplo de script utilizando SQLModel/SQLAlchemy
├── requirements.txt        # Dependências do projeto
├── app/                    # Código fonte do projeto
│   ├── models.py           # Definições de modelos de dados
│   ├── db.py               # Configuração do banco de dados
│   └── main.py             # Lógica principal do projeto
└── .gitignore              # Arquivos a serem ignorados pelo git
```

## **Exemplo de Código**

Abaixo, temos um exemplo básico de como definir um modelo utilizando **SQLModel**:

```python
from sqlmodel import SQLModel, Field, create_engine, Session

class Product(SQLModel, table=True):
    id: int = Field(default=None, primary_key=True)
    name: str
    price: float

# Criação de uma engine e sessão
engine = create_engine("sqlite:///database.db")
SQLModel.metadata.create_all(engine)

# Inserir um novo produto
with Session(engine) as session:
    product = Product(name="Laptop", price=999.99)
    session.add(product)
    session.commit()
```
