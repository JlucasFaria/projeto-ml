# Projeto de Machine Learning

Trabalho da disciplina de Machine Learning com 6 bases de dados públicas:
3 problemas de classificação e 3 problemas de regressão.

## Estrutura

- `dados/` - arquivos das bases de dados
- `notebooks/` - notebooks com o desenvolvimento de cada problema

## Como executar

1. Instalar o Python 3.13
2. Instalar as bibliotecas:

```
pip install -r requirements.txt
```

3. Abrir os notebooks da pasta `notebooks/` no Jupyter, VS Code ou Google Colab e executar as células em ordem.

## Bases de dados

Os arquivos já estão na pasta `dados/`. Também podem ser baixados pelos links oficiais abaixo.

| Notebook | Tipo | Área | Base | Arquivo | Link |
|---|---|---|---|---|---|
| 01_diabetes | Classificação | Saúde | Pima Indians Diabetes | `diabetes.csv` | https://www.openml.org/d/37 |
| 02_inadimplencia | Classificação | Finanças | Default of Credit Card Clients | `credit_card_default.xls` | https://archive.ics.uci.edu/dataset/350/default+of+credit+card+clients |
| 03_marketing_bancario | Classificação | Marketing | Bank Marketing | `bank-full.csv` | https://archive.ics.uci.edu/dataset/222/bank+marketing |
| 04_notas_alunos | Regressão | Educação | Student Performance | `student-mat.csv` | https://archive.ics.uci.edu/dataset/320/student+performance |
| 05_vendas_bigmart | Regressão | Vendas | BigMart Sales | `bigmart_sales.csv` | https://www.kaggle.com/datasets/brijbhushannanda1979/bigmart-sales-data |
| 06_custo_seguro | Regressão | Saúde | Medical Cost Personal | `insurance.csv` | https://www.kaggle.com/datasets/mirichoi0218/insurance |

### Como carregar

```python
import pandas as pd

diabetes = pd.read_csv('../dados/diabetes.csv')
credito = pd.read_excel('../dados/credit_card_default.xls', header=1)
banco = pd.read_csv('../dados/bank-full.csv', sep=';')
alunos = pd.read_csv('../dados/student-mat.csv', sep=';')
vendas = pd.read_csv('../dados/bigmart_sales.csv')
seguro = pd.read_csv('../dados/insurance.csv')
```

Observações:
- `credit_card_default.xls`: a primeira linha do arquivo é um título, por isso o `header=1`.
- `bank-full.csv` e `student-mat.csv` usam `;` como separador.
- `bank-full.csv` foi extraído do arquivo `bank.zip` dentro do download da UCI.
- `student-mat.csv` foi extraído do arquivo `student.zip` dentro do download da UCI (alunos da disciplina de matemática).
- `bigmart_sales.csv` é o arquivo `Train.csv` do Kaggle. O `Test.csv` não foi usado porque não tem a coluna de vendas.
