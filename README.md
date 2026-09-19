Acima de 20 dias de atraso no pagamento, o cancelamento é praticamente garantido.

**Ação sugerida:** tratar 15 dias de atraso como alerta vermelho.

### Demais variáveis analisadas

As demais colunas da base também foram analisadas graficamente, mas não mostraram um padrão tão claro em relação ao cancelamento:

<table>
<tr>
<td><img src="imagens/idade.png" width="440"/></td>
<td><img src="imagens/sexo.png" width="440"/></td>
</tr>
<tr>
<td><img src="imagens/tempo_como_cliente.png" width="440"/></td>
<td><img src="imagens/frequencia_uso.png" width="440"/></td>
</tr>
<tr>
<td><img src="imagens/assinatura.png" width="440"/></td>
<td><img src="imagens/total_gasto.png" width="440"/></td>
</tr>
<tr>
<td><img src="imagens/meses_ultima_interacao.png" width="440"/></td>
<td><img src="imagens/cancelou.png" width="440"/></td>
</tr>
</table>

## Resultado da simulação

Depois de identificados os três fatores acima, a base foi filtrada removendo os clientes com contrato mensal, mais de 5 ligações ao callcenter ou mais de 20 dias de atraso, simulando o que aconteceria se esses três problemas fossem resolvidos:

| | Antes | Depois |
| --- | --- | --- |
| Clientes na base | 309.998 | 171.599 |
| Taxa de cancelamento | 56,72% | 21,82% |
| Taxa de retenção | 43,28% | 78,18% |

Resolver esses três problemas reduziria a taxa de cancelamento em mais da metade, de 56,72% para 21,82%.

## Como executar o projeto

```bash
pip install pandas plotly
jupyter notebook inicial.ipynb
```

O notebook espera encontrar o arquivo `cancelamentos_amostra.csv` na mesma pasta.
