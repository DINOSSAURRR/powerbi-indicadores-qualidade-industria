 Medidas DAX 

```DAX
Faturamento Total =
CALCULATE(
    SUM(fato_faturamento[valor_nf]),
    fato_faturamento[status_nf] = "Emitida"
)
```

```DAX
Qtd NF Emitidas =
CALCULATE(
    COUNTROWS(fato_faturamento),
    fato_faturamento[status_nf] = "Emitida"
)
```

```DAX
Qtd CATs Abertas = COUNTROWS(fato_cat)
```

```DAX
Qtd Orcamentos Enviados =
CALCULATE(
    COUNTROWS(fato_orcamentos),
    fato_orcamentos[status_orcamento] = "Enviado"
)
```

```DAX
Qtd NF Compra MP =
DISTINCTCOUNT(fato_compra_mp[numero_nf_compra])
```

```DAX
Qtd Recusas MP = COUNTROWS(fato_recusa_recebimento)
```

```DAX
Qtd Recl Servico = COUNTROWS(fato_reclamacao_servico)
```

```DAX
Energia Valor Gasto = SUM(fato_energia[valor_gasto])
```

```DAX
Energia kWh Consumido = SUM(fato_energia[kwh_consumido])
```

```DAX
Qtd Admissoes =
CALCULATE(
    COUNTROWS(fato_movimentacao_rh),
    fato_movimentacao_rh[tipo_movimentacao] = "Admissão"
)
```

```DAX
Qtd Demissoes =
CALCULATE(
    COUNTROWS(fato_movimentacao_rh),
    fato_movimentacao_rh[tipo_movimentacao] = "Demissão"
)
```

```DAX
Saldo Movimentacao = [Qtd Admissoes] - [Qtd Demissoes]
```

```DAX
Custo Medio kWh =
DIVIDE([Energia Valor Gasto], [Energia kWh Consumido])
```
