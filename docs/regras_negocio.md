# Regras de Negócio

## RN01 — Faturamento
O faturamento será calculado pela soma de `valor_nf` apenas para registros com `status_nf = "Emitida"`.

## RN02 — Número de NF emitidas
Será calculado pela contagem de notas emitidas. Como o grão da `fato_faturamento` é 1 linha = 1 NF, a contagem de linhas emitidas é suficiente.

## RN03 — Acidente de trabalho
Será medido pela quantidade de CATs registradas na `fato_cat` no período filtrado.

## RN04 — Número de orçamentos enviados
Será medido pela contagem de registros com `status_orcamento = "Enviado"`.

## RN05 — Número de NF de aquisição de matéria-prima
Será medido pela contagem distinta de `numero_nf_compra` na `fato_compra_mp`.

## RN06 — Recusa de matéria-prima no recebimento
Será considerada quando existir registro na `fato_recusa_recebimento`, com detalhamento de fornecedor, NF e item.

## RN07 — Recusas/Reclamações de serviços prestados
Serão contabilizadas pela quantidade de registros na `fato_reclamacao_servico`, podendo ser segmentadas por tipo e classificação.

## RN08 — Energia elétrica
Os indicadores de energia serão apurados por competência mensal:
- valor gasto = soma de `valor_gasto`
- consumo = soma de `kwh_consumido`

## RN09 — Admissões e demissões
Serão apuradas pela coluna `tipo_movimentacao` na `fato_movimentacao_rh`.

## RN10 — Chave temporal
Todas as fatos devem estar relacionadas à `dim_tempo` por `data_id` para permitir análises mensais, trimestrais e anuais.
