# Arquitetura do Projeto

## Objetivo
Disponibilizar uma base analítica para um dashboard gerencial em Power BI Desktop, consolidando indicadores de faturamento, SST, suprimentos, energia e RH.

## Fluxo de dados
1. **Origem**: arquivo Excel `data/base_indicadores.xlsx`
2. **Tratamento**: Power Query
3. **Modelo analítico**: Star Schema
4. **Consumo**: páginas do dashboard no Power BI

```text
Excel -> Power Query -> Modelo Dimensional -> DAX -> Dashboard
```

## Camadas
- **Camada de dados**: planilha com dimensões e fatos
- **Camada semântica**: relacionamentos, hierarquias e medidas DAX
- **Camada de apresentação**: dashboards por tema (Executivo, Comercial/Fiscal, SST, Suprimentos, Energia e RH)

## Boas práticas adotadas
- Separação entre fatos e dimensões
- Uso de `data_id` para integração temporal
- Chaves substitutas inteiras para facilitar relacionamentos
- Dados fictícios coerentes para portfólio
