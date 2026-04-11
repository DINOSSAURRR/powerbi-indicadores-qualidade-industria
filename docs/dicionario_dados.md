# Dicionário de Dados

## Dimensões

### dim_tempo
| Campo | Tipo | Descrição |
|---|---|---|
| data_id | inteiro | Chave no formato AAAAMMDD |
| data | data | Data completa |
| dia | inteiro | Dia do mês |
| mes | inteiro | Número do mês |
| nome_mes | texto | Nome do mês |
| trimestre | texto | Trimestre |
| semestre | texto | Semestre |
| ano | inteiro | Ano |
| ano_mes | texto | Ano e mês |
| numero_semana | inteiro | Semana do ano |
| dia_semana | texto | Nome do dia |

### dim_cliente
| Campo | Tipo | Descrição |
|---|---|---|
| cliente_id | inteiro | Identificador do cliente |
| nome_cliente | texto | Razão social |
| nome_fantasia | texto | Nome fantasia |
| cnpj_cpf | texto | Documento do cliente |
| cidade | texto | Cidade |
| estado | texto | UF |
| segmento | texto | Segmento de mercado |
| status_cliente | texto | Ativo/Inativo |

### dim_fornecedor
| Campo | Tipo | Descrição |
|---|---|---|
| fornecedor_id | inteiro | Identificador do fornecedor |
| nome_fornecedor | texto | Nome/Razão social |
| cnpj | texto | Documento |
| cidade | texto | Cidade |
| estado | texto | UF |
| categoria_fornecedor | texto | Categoria do fornecimento |
| status_fornecedor | texto | Ativo/Inativo |

### dim_funcionario
| Campo | Tipo | Descrição |
|---|---|---|
| funcionario_id | inteiro | Identificador do funcionário |
| nome_funcionario | texto | Nome completo |
| matricula | texto | Matrícula |
| setor_id | inteiro | Referência ao setor |
| cargo | texto | Cargo atual |
| data_admissao | data | Data de admissão |
| status_funcionario | texto | Ativo/Inativo |

### dim_setor
| Campo | Tipo | Descrição |
|---|---|---|
| setor_id | inteiro | Identificador do setor |
| nome_setor | texto | Nome do setor |
| tipo_setor | texto | Operacional/Administrativo |

### dim_item
| Campo | Tipo | Descrição |
|---|---|---|
| item_id | inteiro | Identificador do item |
| codigo_item | texto | Código interno |
| descricao_item | texto | Descrição do item |
| grupo_item | texto | Grupo |
| unidade_medida | texto | Unidade |
| especificacao | texto | Especificação técnica |

### dim_unidade
| Campo | Tipo | Descrição |
|---|---|---|
| unidade_id | inteiro | Identificador da unidade |
| nome_unidade | texto | Nome da unidade/planta |
| cidade | texto | Cidade |
| estado | texto | UF |
| tipo_unidade | texto | Matriz/Filial |

### dim_tipo_ocorrencia
| Campo | Tipo | Descrição |
|---|---|---|
| tipo_ocorrencia_id | inteiro | Identificador |
| categoria | texto | Macrogrupo da ocorrência |
| subcategoria | texto | Tipo específico |
| classificacao | texto | Nível/criticidade |

## Fatos

### fato_faturamento
| Campo | Tipo | Descrição |
|---|---|---|
| faturamento_id | inteiro | Identificador da linha |
| data_id | inteiro | FK tempo |
| unidade_id | inteiro | FK unidade |
| cliente_id | inteiro | FK cliente |
| numero_nf | texto | Número da NF |
| serie_nf | texto | Série da nota |
| valor_nf | decimal | Valor da nota |
| status_nf | texto | Emitida/Cancelada |
| tipo_documento | texto | Tipo de documento fiscal |
| observacao | texto | Informação adicional |

### fato_orcamentos
| Campo | Tipo | Descrição |
|---|---|---|
| orcamento_id | inteiro | Identificador |
| data_id | inteiro | FK tempo |
| unidade_id | inteiro | FK unidade |
| cliente_id | inteiro | FK cliente |
| numero_orcamento | texto | Número do orçamento |
| valor_orcado | decimal | Valor orçado |
| status_orcamento | texto | Enviado/Aprovado/Reprovado |
| canal_envio | texto | Canal de envio |
| responsavel_envio | texto | Responsável pelo envio |

### fato_cat
| Campo | Tipo | Descrição |
|---|---|---|
| cat_id | inteiro | Identificador |
| data_id | inteiro | FK tempo |
| unidade_id | inteiro | FK unidade |
| funcionario_id | inteiro | FK funcionário |
| setor_id | inteiro | FK setor |
| numero_cat | texto | Número/identificação da CAT |
| tipo_acidente | texto | Típico/Trajeto/etc |
| houve_afastamento | texto | Sim/Não |
| dias_afastamento | inteiro | Dias afastado |
| descricao_resumida | texto | Resumo da ocorrência |
| status_cat | texto | Aberta/Fechada |

### fato_compra_mp
| Campo | Tipo | Descrição |
|---|---|---|
| compra_mp_id | inteiro | Identificador |
| data_id | inteiro | FK tempo |
| unidade_id | inteiro | FK unidade |
| fornecedor_id | inteiro | FK fornecedor |
| item_id | inteiro | FK item |
| numero_nf_compra | texto | NF de compra |
| serie_nf_compra | texto | Série |
| quantidade | decimal | Quantidade comprada |
| valor_unitario | decimal | Valor unitário |
| valor_total_item | decimal | Valor do item |
| valor_total_nf | decimal | Valor total da NF |
| status_recebimento | texto | Recebido/Parcial/Recusado |

### fato_recusa_recebimento
| Campo | Tipo | Descrição |
|---|---|---|
| recusa_recebimento_id | inteiro | Identificador |
| data_id | inteiro | FK tempo |
| unidade_id | inteiro | FK unidade |
| fornecedor_id | inteiro | FK fornecedor |
| item_id | inteiro | FK item |
| numero_nf | texto | NF vinculada |
| quantidade_recusada | decimal | Quantidade recusada |
| motivo_recusa | texto | Motivo da recusa |
| tipo_recusa | texto | Qualidade/Documental |
| observacao | texto | Complemento |

### fato_reclamacao_servico
| Campo | Tipo | Descrição |
|---|---|---|
| reclamacao_servico_id | inteiro | Identificador |
| data_id | inteiro | FK tempo |
| unidade_id | inteiro | FK unidade |
| cliente_id | inteiro | FK cliente |
| tipo_ocorrencia_id | inteiro | FK tipo de ocorrência |
| tipo_ocorrencia | texto | Reclamação/Recusa |
| classificacao | texto | Nível da ocorrência |
| descricao_ocorrencia | texto | Descrição |
| status_tratativa | texto | Situação da tratativa |
| responsavel_tratativa | texto | Área responsável |

### fato_energia
| Campo | Tipo | Descrição |
|---|---|---|
| energia_id | inteiro | Identificador |
| data_id | inteiro | FK tempo |
| unidade_id | inteiro | FK unidade |
| competencia | texto | Competência AAAA-MM |
| valor_gasto | decimal | Valor da fatura |
| kwh_consumido | decimal | Consumo em kWh |
| concessionaria | texto | Concessionária |
| observacao | texto | Complemento |

### fato_movimentacao_rh
| Campo | Tipo | Descrição |
|---|---|---|
| movimentacao_rh_id | inteiro | Identificador |
| data_id | inteiro | FK tempo |
| unidade_id | inteiro | FK unidade |
| funcionario_id | inteiro | FK funcionário |
| setor_id | inteiro | FK setor |
| tipo_movimentacao | texto | Admissão/Demissão |
| cargo | texto | Cargo na data do evento |
| motivo_demissao | texto | Motivo, quando aplicável |
| observacao | texto | Complemento |
