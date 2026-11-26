# Roteiro do vídeo (máx. 5 min — tela + voz)

Meta: **~4m30s**, deixando folga. Notebook `projeto_visualizacao_ecommerce.ipynb` já executado, gráficos visíveis, Jupyter em tela cheia. Mostre o código de cada célula antes do gráfico (o professor pede apresentação técnica *e* conceitual).

| Tempo | Tela | Fala |
|---|---|---|
| **0:00–0:30** Abertura | Célula 1 (markdown) | "Olá, sou [nome], da disciplina Visualização da Informação. Usei o dataset *E-commerce Orders and Customer Analytics*, do Kaggle: 1.200 pedidos entre janeiro de 2023 e junho de 2025. Fiz três gráficos de unidades diferentes, ligados por uma pergunta: *de onde vem a receita, como ela evolui e quanto dela realmente se concretiza?*" |
| **0:30–1:00** Dados | Célula de carga | "Li a planilha com `read_excel`. O arquivo tem extensão `.csv`, mas o conteúdo é Excel. Traduzi status, pagamento e produto para português. Conferi que não há pedidos duplicados nem nulos em `TotalPrice`. Aqui 'receita' é a soma de `TotalPrice` de todos os pedidos, inclusive cancelados e devolvidos. O dataset não informa a moeda." |
| **1:00–2:00** Gráfico 1: barras | Código, depois o gráfico (passe o mouse numa barra) | "Estatística descritiva. A receita é uma soma por categoria discreta, o produto, então barras são adequadas: comparo comprimentos a partir da mesma base. Agrupei por produto com `groupby` e ordenei do maior para o menor. No hover aparecem número de pedidos e ticket médio. Cadeira e Impressora empatam na liderança, com cerca de 195,6 mil. Celular é o último, com 151,7 mil e o menor ticket médio. A receita é bem distribuída entre os produtos." |
| **2:00–3:00** Gráfico 2: linhas | Código, depois o gráfico (arraste o range slider) | "Unidade temporal. Agreguei por mês com `resample`. Uso linha porque o tempo é contínuo e a ordem importa. A média móvel de 3 meses, em vermelho, suaviza a oscilação. O pico é junho de 2024, com 68 mil, e o vale é abril de 2023, com 27,8 mil. Os primeiros semestres de 2023 e 2024 foram mais fortes que o de 2025. O slider permite dar zoom em qualquer período." |
| **3:00–4:00** Gráfico 3: sunburst | Código, depois o gráfico (clique numa fatia para expandir) | "Unidade hierárquica. Cada pedido tem status, forma de pagamento e produto, uma hierarquia natural. O ângulo de cada fatia é a receita e a cor indica o status: verde entregue, azul enviado, cinza pendente, vermelho cancelado, laranja devolvido. O resultado principal: só 38,6% da receita vem de pedidos entregues ou enviados. 41,1% está em pedidos cancelados ou devolvidos, e 20,3% está pendente. É a parte que as barras e a linha não mostravam." |
| **4:00–4:30** Fechamento | Célula de conclusão | "Resumindo: as barras mostram *de onde* vem a receita, a linha mostra *quando*, e o sunburst mostra *quanto se concretiza*. Uma ressalva: os dados parecem sintéticos, com distribuição quase uniforme, então as diferenças entre produtos são pequenas e não tirei conclusões fortes delas. Obrigado." |

## Antes de gravar

1. Execute o notebook (*Restart & Run All*) e confira que os números dos gráficos batem com a fala. Se algum for diferente, vale o que o gráfico mostrar.
2. Feche abas e notificações. Grave só a tela e a voz, no Loom ou no YouTube. No YouTube, deixe o vídeo como "não listado" e teste o link em uma aba anônima.
3. Ensaie uma vez com cronômetro. Se passar de 5 minutos, corte a explicação do código de carga (0:30–1:00).

## Para o PDF

- Link do dataset: https://www.kaggle.com/datasets/hammadansari7/e-commerce-orders-and-customer-analytics-dataset
- Link do vídeo: _preencher depois de gravar_
- Gráficos: `graficos/1_barras_receita_por_produto.png`, `graficos/2_linhas_receita_mensal.png`, `graficos/3_sunburst_status_pagamento_produto.png`
- Enviar o PDF e o `.ipynb` separados, sem zip. Prazo: 01/12/2026, 23h59 (Brasília).
