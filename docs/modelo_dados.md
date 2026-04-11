# Modelo de Dados

## Estratégia
O projeto utiliza **modelagem dimensional** no padrão **Star Schema**.

## Dimensões
- `dim_tempo`
- `dim_cliente`
- `dim_fornecedor`
- `dim_funcionario`
- `dim_setor`
- `dim_item`
- `dim_unidade`
- `dim_tipo_ocorrencia`

## Fatos
- `fato_faturamento` — 1 linha = 1 NF emitida
- `fato_orcamentos` — 1 linha = 1 orçamento
- `fato_cat` — 1 linha = 1 CAT aberta
- `fato_compra_mp` — 1 linha = 1 item da NF de compra
- `fato_recusa_recebimento` — 1 linha = 1 item recusado
- `fato_reclamacao_servico` — 1 linha = 1 ocorrência
- `fato_energia` — 1 linha = 1 competência mensal por unidade
- `fato_movimentacao_rh` — 1 linha = 1 movimentação de RH

## Relacionamentos principais
```text
dim_tempo -> todas as fatos
dim_cliente -> fato_faturamento, fato_orcamentos, fato_reclamacao_servico
dim_fornecedor -> fato_compra_mp, fato_recusa_recebimento
dim_funcionario -> fato_cat, fato_movimentacao_rh
dim_setor -> fato_cat, fato_movimentacao_rh
dim_item -> fato_compra_mp, fato_recusa_recebimento
dim_unidade -> todas as fatos
dim_tipo_ocorrencia -> fato_reclamacao_servico
```

## Racional técnico
O modelo foi separado por processo de negócio para:
- evitar duplicidade de granularidade
- simplificar as medidas DAX
- melhorar performance e manutenção no Power BI
