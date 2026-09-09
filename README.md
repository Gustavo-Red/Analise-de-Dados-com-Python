# Análise de Cancelamento de Clientes (Churn Analysis)

Projeto de análise de dados utilizando Python com foco na identificação de padrões de cancelamento de clientes (churn) e proposição de ações para redução desse índice.

---

## Contexto do Projeto

Neste projeto, atuo como analista de dados em uma empresa com mais de **300 mil clientes**, que enfrenta um problema significativo de cancelamento de serviços.

A empresa identificou que grande parte da sua base tornou-se inativa, impactando diretamente seus resultados. Diante disso, surge a necessidade de compreender, por meio de dados, **quais fatores estão levando os clientes a cancelarem**.

---

## Objetivo

- Identificar os principais fatores que levam ao cancelamento de clientes  
- Analisar padrões de comportamento dos usuários  
- Gerar insights para auxiliar na tomada de decisão  
- Propor ações estratégicas para reduzir o churn  

---

## Tecnologias Utilizadas

- Python  
- Pandas  
- Plotly  

---

## Estrutura do Projeto

- `inicial.ipynb` → Notebook com toda a análise de dados  
- `cancelamentos_amostra.csv` → Amostra da base de dados  
- `imagens/` → Gráficos exportados da análise  

---

## Etapas da Análise

### 1. Tratamento de dados
- Remoção de colunas irrelevantes  
- Tratamento de valores nulos  
- Limpeza da base  

### 2. Análise exploratória
- Cálculo da taxa de cancelamento  
- Comparação entre clientes ativos e cancelados  

### 3. Visualização de dados
- Construção de gráficos interativos  
- Identificação de padrões relevantes  

---

## Principais Insights

### Contrato Mensal x Cancelamento
![Gráfico - Duração do Contrato](imagens/grafico_duracao_contrato.png)

Clientes com contrato mensal apresentam taxa de cancelamento muito acima dos demais. Praticamente todos os clientes que cancelaram estavam nesse tipo de contrato.

### Ligações ao Call Center x Cancelamento
![Gráfico - Ligações Call Center](imagens/grafico_ligacoes_callcenter.png)

Clientes que ligam mais de 4 vezes para o call center têm forte tendência ao cancelamento — a partir de 3 ligações já é considerado um sinal de alerta.

### Atraso no Pagamento x Cancelamento
![Gráfico - Dias de Atraso](imagens/grafico_dias_atraso.png)

Atrasos acima de 20 dias estão fortemente associados ao cancelamento. Atrasos a partir de 15 dias já indicam risco elevado.

---

## Estimativa de Melhora

Ao simular a resolução dos três problemas acima (removendo contratos mensais, limitando ligações ao call center e atrasos de pagamento), a taxa de cancelamento estimada cai de forma expressiva em relação ao cenário original, mostrando o impacto potencial de ações direcionadas a essas três causas.

---

## Base de Dados

A base de dados original contém mais de **800 mil registros**.

Devido às limitações de upload do GitHub, foi utilizada uma **amostra com mais de 300 mil registros**, mantendo um volume significativo e representativo para a análise.

---

## Como Executar

1. Instale as dependências em um ambiente virtual:

```bash
pip install pandas plotly kaleido
```

2. Execute o notebook:

```bash
inicial.ipynb
```
