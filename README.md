# Data Pipeline: TripData Analysis with Metabase

Este projeto consiste em um pipeline de dados que processa dados de viagens (CSV), armazena-os em um banco de dados PostgreSQL via Docker e disponibiliza as informações para visualização no Metabase.

## 🚀 Tecnologias Utilizadas

* **Banco de Dados:** PostgreSQL 15 (via Docker)
* **Ferramenta de BI:** Metabase (via Docker)
* **IDE:** Visual Studio Code
* **Docker & Docker Compose:** Gerenciamento de infraestrutura.
* **Python (Pandas & SQLAlchemy):** Tratamento de dados e carga (ETL).
* **Orquestração:** Docker Compose

## 📂 Estrutura do Repositório

```bash
.
├── data/                 # Arquivos CSV originais
├── notebooks/            # Jupyter Notebooks para ETL e análise
├── docker-compose.yaml   # Orquestração dos containers (Postgres + Metabase)
├── requirements.txt      # Dependências Python
└── LICENSE               # Licença do projeto
```

## 🛠️ Configuração do Ambiente

Para reproduzir este ambiente, você precisará do Docker e Docker Desktop instalados, Python 3.x instalado.

1-  Variáveis de Ambiente

Crie um arquivo .env na raiz da pasta do curso com as seguintes definições:

```bash
DB_USER=seu_usuario
DB_PASSWORD=sua_senha

```

2- Subir o banco de dados

```bash
docker-compose up -d

```

3 - Preparar ambiente Python

```bash
python -m venv .venv #Cria o ambiente virtual

pip install -r requirements.txt #Intala as dependencias

```

4 - Processamento

Abra o arquivo notebooks/main.ipynb e execute as células. O fluxo do notebook realiza:

    * Leitura do arquivo data/yellow_tripdata_2016-03.csv.
    * Limpeza e tipagem dos dados com Pandas.
    * Carga dos dados no Postgres utilizando to_sql.

## 📊 Configuração no Metabase

Após os dados serem carregados via Python:

1 - Acesse http://localhost:3000.

2 - Siga os passos iniciais de configuração.

3 - Ao adicionar o banco de dados, use as seguintes credenciais:

    * Tipo de Banco: PostgreSQL
    * Host: db (Se estiver conectando de dentro da rede Docker) ou localhost (se o Metabase for local).
    * Porta: 5432
    * Banco de Dados: (O nome definido no seu .env/docker-compose)
    * Usuário/Senha: (Definidos no seu .env/docker-compose)

## 📝 Notas de Estudo

**Persistência**: Os dados são persistidos localmente na pasta postgres_data_project/. 

**Desativar container**: Após o uso, utilize ```bash docker-compose down ``` para desativar o container. Seu progresso não será perdido.

**Outros acessos**: Sempre quando for estudar novamente, basta rodar o ```bash docker-compose up -d ```
