# Visualização da Informação — Análise de Pedidos de E-commerce

Projeto da disciplina de Visualização da Informação (prof. Ismar Frango).
Três gráficos Plotly, cada um de uma unidade diferente da disciplina, sobre um mesmo dataset real de pedidos de e-commerce (1.200 pedidos, jan/2023 a jun/2025). Juntos contam uma narrativa: *de onde vem a receita, como ela evolui e quanto dela se concretiza.*

| # | Gráfico | Unidade | O que mostra |
|---|---------|---------|--------------|
| 1 | Barras | Estatística descritiva | Receita por produto (ticket médio e nº de pedidos no hover) |
| 2 | Linhas | Temporal | Receita mensal + média móvel de 3 meses, com range slider |
| 3 | Sunburst | Hierárquica | `status > pagamento > produto`, tamanho = receita, cor = ticket médio |

"Receita" = soma de `TotalPrice` de todos os pedidos, inclusive cancelados e devolvidos. O dataset não informa a moeda.

## Arquivos

- `projeto_visualizacao_ecommerce.ipynb` — código único da entrega
- `data/ecommerce/ecommerce_orders_dataset.csv.xlsx` — dataset ([Kaggle: E-commerce Orders and Customer Analytics](https://www.kaggle.com/datasets/hammadansari7/e-commerce-orders-and-customer-analytics-dataset)); apesar do `.csv` no nome, é um arquivo Excel
- `projeto_visualizacao_usd_brl.ipynb` + `data/USD_BRL_hist.csv` — versão anterior (USD/BRL), mantida só como reserva; não faz parte da entrega

## Como executar

Dependências: `pandas`, `plotly`, `nbformat`, `openpyxl` e Jupyter. Execute a partir da raiz do repositório (o notebook lê os dados por caminho relativo):

```powershell
.venv/Scripts/python.exe -m jupyter lab projeto_visualizacao_ecommerce.ipynb
```

Para executar de ponta a ponta sem abrir a interface:

```powershell
.venv/Scripts/python.exe -m jupyter nbconvert --to notebook --execute projeto_visualizacao_ecommerce.ipynb --output projeto_visualizacao_ecommerce_executado.ipynb
```

(`*_executado.ipynb` é ignorado pelo git.)

Para baixar o dataset novamente (requer a CLI `kaggle` e o token na variável de ambiente `KAGGLE_API_TOKEN`):

```powershell
kaggle datasets download hammadansari7/e-commerce-orders-and-customer-analytics-dataset -p data/ecommerce --unzip
```

## Entrega

Prazo: 01/12/2026, 23:59 (Brasília). Um arquivo de código + um PDF (link do dataset, link do vídeo de até 5 min e os três gráficos), sem zip.