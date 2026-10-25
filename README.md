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

Observações:
- Cada notebook é independente e pode ser executado separadamente.
- Os notebooks leem os dados com o caminho `../dados/`, então a estrutura de pastas deve ser mantida. No Google Colab é preciso enviar a pasta `dados` junto e ajustar o caminho, se necessário.
- Todos os modelos e divisões de treino/teste usam `random_state=42`, então os resultados são os mesmos a cada execução.
- O notebook `03_marketing_bancario` é o mais demorado (alguns minutos), por causa do SVM em uma base grande.

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

## Modelos utilizados

- **Classificação:** Regressão Logística, KNN, Árvore de Decisão, Random Forest e SVM
- **Regressão:** Regressão Linear, Ridge, Árvore de Decisão, Random Forest e KNN

## Resumo dos resultados

### Classificação

| Notebook | Pergunta | Melhor modelo | Acurácia | Precisão | Recall | F1-score |
|---|---|---|---|---|---|---|
| 01_diabetes | É possível prever se uma paciente tem diabetes? | Random Forest | 0,773 | 0,702 | 0,611 | 0,653 |
| 02_inadimplencia | É possível prever se um cliente vai deixar de pagar a fatura? | Árvore de Decisão | 0,816 | 0,655 | 0,357 | 0,462 |
| 03_marketing_bancario | É possível prever se um cliente vai aceitar a oferta da campanha? | Random Forest | 0,893 | 0,613 | 0,223 | 0,327 |

### Regressão

| Notebook | Pergunta | Melhor modelo | MAE | RMSE | R² |
|---|---|---|---|---|---|
| 04_notas_alunos | É possível prever a nota final de um aluno? | Random Forest | 0,60 | 0,82 | 0,930 |
| 05_vendas_bigmart | É possível prever o valor de venda de um produto em uma loja? | Random Forest | 716 | 1.026 | 0,613 |
| 06_custo_seguro | É possível prever o custo médico anual de uma pessoa? | Random Forest | 2.413 | 4.241 | 0,902 |

Principais observações:
- Nas bases de inadimplência e marketing, as classes são desbalanceadas, então a acurácia parece alta, mas o recall mostra que os modelos ainda deixam passar muitos casos positivos.
- Na base de notas, o resultado alto depende quase totalmente da nota do 2º período (G2). Sem as notas anteriores, o R² cai para cerca de 0,21.
- Na base de seguro, os modelos de árvore foram melhores que a regressão linear porque conseguem capturar a combinação entre ser fumante e ter IMC alto.

A análise completa de cada problema, com gráficos e conclusões, está nos notebooks.
