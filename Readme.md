---
# **ANÁLISE HISTÓRICA DO VALOR DE AÇÕES E PAGAMENTO DE DIVIDENDOS**
---

# **Introdução**

Nesse código vamos buscar dados históricos de valor de ações e dividendos pagos de uma série de ações listadas na bolsa de valores. Me limitei a um período de 10 anos, mas se interessando por período diferente, isso pode ser facilmente alterado no código.

Dividi o script em dois blocos:

- Bloco 1 - Valor médio das ações por ano.
- Bloco 2 - Total de dividendos pagos por cota de ação por ano.

Juntei aqui as principais empresas pagadoras de dividendos, segundo o site **Investidor 10**. A lista esta disponível nesse link https://investidor10.com.br/acoes/rankings/maiores-dividend-yield/.

Vamos usar aqui a biblioteca **yfinance**. O yfinance não é afiliado, ou verificado pelo Yahoo, é apenas uma ferramenta de código aberto que usa APIs disponíveis publicamente do Yahoo e se destina a fins educacionais e de pesquisa.

Caso tenha interesse pelo assunto, tenho outro repositório disponível em que fiz uma análise mais aprofundada por ações individuais, permitindo exportar os dados em um PDF, nesse link: https://github.com/mauriciosangiogo/Analise-de-acoes-da-Bolsa-de-Valores-B3-com-Python.git.
# Analise_historica_preco_acoes_e_pagamento_de_dividendos
