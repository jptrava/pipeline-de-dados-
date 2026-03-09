# Pipeline de Dados: CSV para SQLite 🚀

Este projeto consiste em um pipeline de dados (ETL) desenvolvido em Python que extrai dados de produção de alimentos de um arquivo CSV, realiza transformações e limpezas específicas e os carrega em um banco de dados relacional SQLite.

## 📌 Objetivo
Automatizar o processo de ingestão de dados brutos, aplicando regras de negócio e garantindo que as informações estejam estruturadas para futuras análises de Business Intelligence (BI).

## 🛠️ Tecnologias e Ferramentas
- **Linguagem:** Python 3.12+
- **Bibliotecas:** `csv` (extração), `sqlite3` (carga e persistência)
- **Banco de Dados:** SQLite
- **Visualização:** DB Browser for SQLite

## ⚙️ O Fluxo ETL

### 1. Extração (Extract)
O script realiza a leitura do arquivo `producao_alimentos.csv`, que contém registros brutos de produtos, quantidades, preços e receitas.

### 2. Transformação (Transform)
Durante o processamento, foram aplicadas as seguintes lógicas:
- **Limpeza Numérica:** Remoção de caracteres de formatação (pontos) para garantir a conversão correta para tipos numéricos (`float`/`int`).
- **Filtro de Qualidade:** Apenas registros com quantidade produzida superior a **10 unidades** são carregados no banco.
- **Enriquecimento de Dados:** Cálculo dinâmico da coluna **Margem de Lucro**, agregando valor analítico ao dado antes de sua carga final.

### 3. Carga (Load)
Os dados transformados são inseridos em uma tabela chamada `producao` dentro do banco de dados `dsadb.db`. O script garante a idempotência ao recriar a tabela a cada execução (`DROP TABLE IF EXISTS`).

## 📁 Estrutura do Projeto
- `Script.py`: Código principal com a lógica do pipeline.
- `producao_alimentos.csv`: Fonte de dados bruta.
- `dsadb.db`: Arquivo do banco de dados gerado.

