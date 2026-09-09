Projeto de análise de dados - Análise de Cancelamento de Clientes

# Análise de Cancelamento de Clientes (Churn)

## Contexto

Este projeto foi desenvolvido como um estudo prático de análise de dados, utilizando uma base de clientes para investigar os principais fatores relacionados ao cancelamento de serviços.

A empresa possui uma grande quantidade de clientes e identificou uma taxa elevada de cancelamentos. A partir disso, a análise busca entender quais características e comportamentos estão mais associados ao churn e quais ações podem ser tomadas para reduzir esse índice.

---

## Objetivo

Realizar uma análise exploratória dos dados, incluindo:

* leitura e organização da base de dados;
* tratamento de valores ausentes;
* remoção de informações que não contribuem para a análise;
* cálculo da quantidade e da proporção de clientes que cancelaram;
* visualização das variáveis da base;
* identificação dos principais fatores associados ao cancelamento;
* simulação de ações para redução do churn.

---

## Descrição

Análise exploratória de dados de clientes com foco na identificação de padrões de cancelamento e na geração de insights para possíveis estratégias de retenção.

---

## Resultados

### Cancelamento por duração do contrato

![Cancelamento por duração do contrato](images/05_duracao_contrato.png)

O tipo de contrato apresenta um dos padrões mais claros da análise. Na base utilizada, os clientes com contrato **Monthly** aparecem exclusivamente no grupo de cancelamento, enquanto os contratos **Annual** e **Quarterly** apresentam clientes cancelados e não cancelados.

Esse comportamento indica uma forte associação entre contratos mensais e churn.

### Cancelamento por ligações ao Call Center

![Cancelamento por ligações ao Call Center](images/08_ligacoes_callcenter.png)

A quantidade de ligações para o Call Center também apresenta uma diferença significativa entre os grupos.

Até 4 ligações ainda existe uma quantidade relevante de clientes que não cancelaram. A partir de **5 ligações**, os clientes cancelados passam a representar a grande maioria dos registros.

### Cancelamento por dias de atraso

![Cancelamento por dias de atraso](images/07_dias_atraso.png)

Os dias de atraso apresentam outro padrão importante. Até aproximadamente **20 dias de atraso**, os dois grupos ainda estão presentes de forma significativa.

Após esse ponto, o comportamento da base muda e os clientes cancelados passam a predominar, indicando uma forte relação entre atrasos maiores e churn.

### Cancelamento por sexo

![Cancelamento por sexo](images/01_sexo.png)

A distribuição entre homens e mulheres apresenta valores próximos, sem uma diferença expressiva na quantidade de cancelamentos. Dessa forma, o sexo não aparece como um dos principais fatores de diferenciação nesta análise.

### Cancelamento por tipo de assinatura

![Cancelamento por assinatura](images/06_assinatura.png)

As categorias Standard, Basic e Premium apresentam distribuições relativamente semelhantes entre clientes cancelados e não cancelados.

### Cancelamento por frequência de uso

![Cancelamento por frequência de uso](images/09_frequencia_uso.png)

A frequência de uso apresenta sobreposição considerável entre os dois grupos, não mostrando um padrão tão evidente quanto os três principais fatores identificados.

### Cancelamento por tempo como cliente

![Cancelamento por tempo como cliente](images/10_tempo_cliente.png)

O tempo de permanência do cliente também apresenta bastante sobreposição entre os grupos de cancelamento, sem um ponto de separação tão claro.

### Cancelamento por idade

![Cancelamento por idade](images/11_idade.png)

A idade apresenta diferenças na distribuição dos grupos, porém sem um padrão tão direto quanto duração do contrato, ligações ao Call Center e dias de atraso.

### Cancelamento por total gasto

![Cancelamento por total gasto](images/04_total_gasto.png)

A variável de gasto total apresenta diferenças entre os grupos, mas não demonstra um padrão de cancelamento tão evidente quanto os principais fatores encontrados.

### Cancelamento por meses desde a última interação

![Cancelamento por meses desde a última interação](images/03_meses_ultima_interacao.png)

A variável apresenta diferenças na distribuição dos grupos ao longo do período, porém o padrão não é tão evidente quanto nos fatores relacionados ao contrato, atendimento e atraso.

---

## Principais Insights

- **Contrato mensal:** clientes com contrato Monthly apresentam uma associação muito forte com o cancelamento. Uma possível estratégia seria incentivar a migração para contratos de maior duração.

- **Ligações ao Call Center:** a partir de aproximadamente 5 ligações, os cancelamentos passam a predominar fortemente. Isso pode ser utilizado como um indicador para identificar clientes que precisam de atenção antes de cancelar.

- **Dias de atraso:** atrasos superiores a aproximadamente 20 dias estão associados a uma predominância de cancelamentos. A empresa poderia utilizar alertas preventivos e ações de cobrança antes que o atraso atinja esse ponto.

- **Sexo, assinatura e outras variáveis:** embora apresentem diferenças na distribuição, não demonstraram um padrão tão forte quanto os três fatores principais.

---

## Simulação de Redução do Churn

Após identificar os principais fatores associados ao cancelamento, foi realizada uma simulação considerando a remoção de três situações problemáticas:

- clientes com contrato mensal;
- clientes com mais de 4 ligações ao Call Center;
- clientes com mais de 20 dias de atraso.

```python
condicao = tabela["duracao_contrato"] != "Monthly"
tabela = tabela[condicao]

condicao = tabela["ligacoes_callcenter"] <= 4
tabela = tabela[condicao]

condicao = tabela["dias_atraso"] <= 20
tabela = tabela[condicao]
```

A taxa de cancelamento foi calculada novamente após os filtros para observar como a distribuição dos clientes poderia mudar.

Essa etapa representa uma **simulação baseada nos dados**, e não uma previsão de que essas ações necessariamente produzirão o mesmo resultado em um cenário real.

---

## Estrutura do Projeto

- `cancelamentos_amostra.csv` — arquivo com a base de dados utilizada na análise
- `inicial.ipynb` — notebook com o processamento, análise e visualizações
- `README.md` — documentação do projeto
- `images/` — imagens utilizadas na documentação

---

## Tecnologias Utilizadas

- Python 3.12
- Pandas
- Plotly Express
- Jupyter Notebook

---

## Etapas Realizadas

### 1. Leitura dos dados

A base foi carregada a partir do arquivo `cancelamentos_amostra.csv` utilizando a biblioteca `pandas`.

### 2. Limpeza dos dados

Foi removida a coluna `CustomerID`, por não ser relevante para a análise do comportamento dos clientes.

Em seguida, foram removidas linhas com valores ausentes utilizando `dropna()`.

### 3. Análise da variável de cancelamento

A coluna `cancelou` foi utilizada como variável principal da análise:

- `1.0` → cliente que cancelou;
- `0.0` → cliente que não cancelou.

A distribuição dos valores foi calculada utilizando `value_counts()` e `value_counts(normalize=True)`.

### 4. Visualização dos dados

Foram utilizados gráficos de histograma do **Plotly Express** para comparar o comportamento da variável `cancelou` com as demais colunas da base.

A estrutura utilizada permitiu gerar os gráficos de forma automática:

```python
for coluna in tabela.columns:
    grafico = px.histogram(
        tabela,
        x=coluna,
        color="cancelou",
        text_auto="True"
    )

    grafico.show()
```

### 5. Identificação dos fatores de maior impacto

Após a análise dos gráficos, foram identificados três fatores com comportamento mais evidente:

- duração do contrato;
- número de ligações para o Call Center;
- dias de atraso.

### 6. Simulação

Foram aplicados filtros na base para estimar como a distribuição dos cancelamentos poderia se comportar após a redução desses três fatores de risco.

---

## Base de Dados

A análise foi realizada utilizando o arquivo `cancelamentos_amostra.csv`.

A base utilizada contém centenas de milhares de registros, permitindo realizar a análise sobre um volume significativo de clientes.

---

## Como Executar

1. Instale as dependências:

```bash
pip install pandas plotly jupyter
```

2. Abra o notebook:

```bash
jupyter notebook inicial.ipynb
```

3. Execute as células em ordem ou utilize **Run All**.
