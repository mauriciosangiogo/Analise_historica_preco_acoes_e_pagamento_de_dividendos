---
# **ANÁLISE HISTÓRICA DO VALOR DE AÇÕES E PAGAMENTO DE DIVIDENDOS**

<<<<<<< HEAD
=======
---
# **Introdução**
>>>>>>> e09d4fd (Atualizacao do README,md)

Nesse código vamos buscar dados históricos de valor de ações e dividendos pagos de uma série de ações listadas na bolsa de valores. Me limitei a um período de 10 anos, mas se interessando por período diferente, isso pode ser facilmente alterado no código.

Dividi o script em dois blocos:

*   Bloco 1 - Valor médio das ações por ano.
*   Bloco 2 - Total de dividendos pagos por cota de ação por ano.


Juntei aqui as principais empresas pagadoras de dividendos, segundo o site **Investidor 10**. A lista esta disponível nesse link https://investidor10.com.br/acoes/rankings/maiores-dividend-yield/.


Vamos usar aqui a biblioteca **yfinance**. O yfinance não é afiliado, ou verificado pelo Yahoo, é apenas uma ferramenta de código aberto que usa APIs disponíveis publicamente do Yahoo e se destina a fins educacionais e de pesquisa.

Caso tenha interesse pelo assunto, tenho outro repositório disponível em que fiz uma análise mais aprofundada por ações individuais, permitindo exportar os dados em um PDF, nesse link: https://github.com/mauriciosangiogo/Analise-de-acoes-da-Bolsa-de-Valores-B3-com-Python.git.
<<<<<<< HEAD
=======


#**Valor médio das ações por ano**

## **Lista de Temas e Tópicos desse bloco (LTT):**

1 - Importar bibliotecas de interesse.

2 - Informar símbolos das ações de interesse.

3 - Adicionar a terminação ".SA" nesses símbolos, pois as mesmas estão listadas dessa forma no yfinance.

4 - Definir período de tempo.

5 - Buscar dados da valor médio das ações por empresa, por ano.

6 - Organizar os dados em um DataFrame.

7 - Exportar para um arquivo .xlsx (opcional).

```
# 1 - Importar bibliotecas de interesse
import yfinance as yf
import pandas as pd

# 2 - Informar símbolos das ações de interesse
symbols = ['SYNE3', 'ALLD3', 'LEVE3', 'PATI3', 'EVEN3', 'VULC3', 'ANIM3', 'AURE3', 'CMIN3', 'PETR4', 'CSRN3', 'CMIG4', 'CSMG3', 'BRAP4', 'BMGB4', 'WHRL4', 'CGAS3', 'EQPA3', 'PINE4', 'GOAU4', 'CSNA3', 'EKTR3', 'RECV3', 'ODPV3', 'VALE3', 'PGMN3', 'BBDC3', 'CGRA4', 'GEPA4', 'BGIP4', 'TAEE11', 'REDE3', 'CEBR3', 'CSED3', 'BBAS3', 'EMAE4', 'TRPL4', 'SOJA3', 'ETER3', 'TGMA3', 'KEPL3', 'CPFE3', 'SCAR3', 'DIRR3', 'VITT3', 'CURY3', 'MELK3', 'LAVV3', 'VBBR3', 'ROMI3', 'BBSE3', 'BEES3', 'RANI3', 'BAZA3', 'ABCB4', 'SHUL4', 'CEEB3', 'VVEO3', 'JHSF3', 'STBP3', 'TIMS3', 'PORT3', 'ITUB4', 'UNIP6', 'AGRO3', 'POSI3', 'ITSA4', 'POMO4', 'CSUD3', 'EGIE3', 'PFRM3', 'VLID3', 'GRND3', 'MYPK3', 'BNBR3', 'FESA4', 'MTRE3', 'LJQQ3', 'DEXP3', 'JBSS3', 'ABEV3', 'CXSE3', 'SANB11', 'GGBR3', 'FIQE3']

# 3 - Adicionar a terminação ".SA" nesses símbolos, pois as mesmas estão listadas dessa forma no yfinance.
symbols = [symbol + '.SA' for symbol in symbols]

# Dicionário para armazenar os dados
data = {}

# 4 - Definir período de tempo de 10 anos
end_date = pd.Timestamp.now().tz_localize(None)
start_date = end_date - pd.DateOffset(years=10)

# 5 - Buscar dados do valor médio das ações por empresa e por ano
for symbol in symbols:
    stock = yf.Ticker(symbol)

    # Buscar o preço médio anual das ações
    price_yearly = stock.history(period='1d', start=start_date, end=end_date).resample('Y').mean()

    data[symbol] = price_yearly['Close'].to_dict()

# 6 - Organizar os dados em um DataFrame
df = pd.DataFrame(data)
# Transpor para que as empresas estejam nas linhas e os anos nas colunas
df = df.transpose()
# Ordenar colunas do ano menor para o ano maior
df = df[sorted(df.columns)]
# Renomear colunas para manter apenas o ano
df.columns = [int(ano.year) for ano in df.columns]
print(df)

# 7 - Exportar para um arquivo .xlsx (opcional)
df.to_excel('precos_medios_anuais.xlsx', index=True)
```


#**Total de dividendos pagos por cota de ação por ano.**

## **Lista de Temas e Tópicos desse bloco (LTT):**

1 - Importar bibliotecas de interesse.

2 - Informar símbolos das ações de interesse.

3 - Adicionar a terminação ".SA" nesses símbolos, pois as mesmas estão listadas dessa forma no yfinance.

4 - Definir período de tempo.

5 - Buscar dados de dividendos, por empresa, por ano.

6 - Organizar os dados em um DataFrame.

7 - Exportar para um arquivo .xlsx (opcional).

```

# 1 - Importar bibliotecas
import yfinance as yf
import pandas as pd

# 2 - Informar símbolos das ações de interesse
symbols =  ['SYNE3', 'ALLD3', 'LEVE3', 'PATI3', 'EVEN3', 'VULC3', 'ANIM3', 'AURE3', 'CMIN3', 'PETR4', 'CSRN3', 'CMIG4', 'CSMG3', 'BRAP4', 'BMGB4', 'WHRL4', 'CGAS3', 'EQPA3', 'PINE4', 'GOAU4', 'CSNA3', 'EKTR3', 'RECV3', 'ODPV3', 'VALE3', 'PGMN3', 'BBDC3', 'CGRA4', 'GEPA4', 'BGIP4', 'TAEE11', 'REDE3', 'CEBR3', 'CSED3', 'BBAS3', 'EMAE4', 'TRPL4', 'SOJA3', 'ETER3', 'TGMA3', 'KEPL3', 'CPFE3', 'SCAR3', 'DIRR3', 'VITT3', 'CURY3', 'MELK3', 'LAVV3', 'VBBR3', 'ROMI3', 'BBSE3', 'BEES3', 'RANI3', 'BAZA3', 'ABCB4', 'SHUL4', 'CEEB3', 'VVEO3', 'JHSF3', 'STBP3', 'TIMS3', 'PORT3', 'ITUB4', 'UNIP6', 'AGRO3', 'POSI3', 'ITSA4', 'POMO4', 'CSUD3', 'EGIE3', 'PFRM3', 'VLID3', 'GRND3', 'MYPK3', 'BNBR3', 'FESA4', 'MTRE3', 'LJQQ3', 'DEXP3', 'JBSS3', 'ABEV3', 'CXSE3', 'SANB11', 'GGBR3', 'FIQE3']

# 3 - Adicionar a terminação ".SA" nesses símbolos, pois as mesmas estão listadas dessa forma no yfinance.
symbols = [symbol + '.SA' for symbol in symbols]

# Dicionário para armazenar os dados

data = {}

# 4- Definir período de 10 anos
end_date = pd.Timestamp.now().tz_localize(None)
start_date = end_date - pd.DateOffset(years=10)

# 5 - Buscar os dados de dividendos por empresa e por ano
for symbol in symbols:
    stock = yf.Ticker(symbol)
    dividends = stock.dividends

    if not dividends.empty:
        dividends.index = pd.to_datetime(dividends.index)
        dividends.index = dividends.index.tz_localize(None)

        # Agrupar dividendos por ano e calcular soma
        dividends_yearly = dividends.groupby(dividends.index.year).sum()

        data[symbol] = dividends_yearly.to_dict()

# 6 - Organizar os dados em um DataFrame
df = pd.DataFrame(data)
# Transpor para que as empresas estejam nas linhas e os anos nas colunas
df = df.transpose()
# Renomear colunas para anos
df.columns = [f'Dividendos {ano}' for ano in df.columns]
print(df)

# 7 - Exportar para um arquivo .xlsx (opcional).
df.to_excel('dividendos.xlsx', index=True)
```

>>>>>>> e09d4fd (Atualizacao do README,md)
