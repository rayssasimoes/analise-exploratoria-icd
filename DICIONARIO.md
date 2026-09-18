# Pedidos sintéticos

Unidade: um pedido de uma loja fictícia, em abril de 2026. Arquivo UTF-8 com BOM, separador vírgula, ponto decimal e célula vazia para ausente. 62 linhas físicas, 7 colunas.

|Campo|Tipo e unidade|Significado|
|---|---|---|
|pedido_id|identificador|Código do pedido, nunca uma medida para calcular média|
|data|data ISO YYYY-MM-DD|Data do pedido|
|canal|categoria nominal|Pago ou Orgânico|
|categoria|categoria nominal|Livros, Casa ou Tecnologia|
|valor_brl|quantitativa, reais|Valor de pedido concluído; pelo contrato deve ser maior que zero; não inclui estornos|
|entrega_dias|quantitativa, dias|Dias até a entrega; ausente significa não informado, não zero|
|satisfacao|escore de 1 a 5|Escala ordinal sintética com décimos; Pearson é demonstrado com ressalva e Spearman no notebook|

Tratamento de referência: preservar o CSV; retirar uma duplicata exata (P012); separar P061, de -40 reais, como inválido pelo contrato; não remover P048 (2400 reais) automaticamente. Restam 60 pedidos, 30 por canal, com 6 entregas não informadas (10%). Contar ausentes antes de cada cálculo. Para correlação, existem 54 pares completos.

Não há identificação de pessoas reais. O gerador introduz uma associação negativa entre tempo e satisfação e um pedido extremo, sem mecanismo causal real. A atividade é de exploração e auditoria, não de inferência populacional.
