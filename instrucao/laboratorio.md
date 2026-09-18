# Laboratório: IA como copiloto analítico

**Duração:** 40 minutos, em duplas. Uma pessoa propõe a análise; outra verifica. Troquem os papéis na metade.

## Preparação

Baixe `assets/dados/pedidos_sinteticos.csv` e `assets/dados/DICIONARIO.md`. Use uma LLM com análise de arquivos e execução, ou peça código e execute em Jupyter/Colab. Se não houver acesso à LLM, a atividade pode ser feita diretamente em pandas. O notebook de referência requer somente pandas; seus gráficos SVG não dependem de matplotlib.

Anexe apenas o conjunto sintético fornecido. Leia o dicionário. Preserve o arquivo original e trabalhe em uma cópia lógica.

## 0–5 min: pergunta e auditoria

Escolha uma pergunta:

- Como o valor dos pedidos difere entre os canais Pago e Orgânico?
- O que o pedido de R$ 2.400 muda na descrição da loja?
- Como entrega e satisfação se relacionam nos pedidos com informação completa?

Registre a expectativa inicial. Use o prompt `auditoria` de `prompts.md`. Confira unidade de análise, tipos, ausentes, duplicatas exatas, IDs conflitantes e valores inválidos. Anote cada filtro e o número de linhas antes e depois. A base deve chegar a 60 pedidos sem remover o pedido alto.

## 5–25 min: explorar com evidência

1. Gere contagens por canal e um resumo de valor_brl: n, média, mediana, desvio-padrão, Q1, Q3 e IQR. Declare ddof=1 e quartis por interpolação linear.
2. Escolha dois gráficos que respondam à sua pergunta. Inclua eixos, unidades, n e fonte. Sugestões: histograma + boxplot por canal; dispersão + resumo por canal; receita diária + histograma.
3. Investigue uma anomalia ou padrão. Para o IQR, liste o ID sinalizado e compare cenários com e sem ele, mantendo a base principal. Para correlação, declare pares completos e compare a leitura visual com os coeficientes.
4. Guarde os prompts, o código efetivamente executado e as saídas. Se a LLM não tiver executado, não trate seu texto como resultado calculado.

## 25–35 min: revisão cruzada

Troque com outra dupla. Use o prompt `auditor`. Confira pelo menos três números com cálculo independente: média por soma/n, mediana por ordenação e um quartil ou contagem.

Verifique: os gráficos escondem observações? O número de pares da correlação está explícito? Algum outlier foi apagado sem evidência? Alguma associação foi escrita como causa? Uma explicação foi apresentada como fato sem dados de apoio?

## 35–40 min: relato

Entregue notebook ou script, dois gráficos, registro dos filtros e um parágrafo com:

> **Observamos:** resultado numérico e visual. **Uma hipótese:** explicação ainda não demonstrada. **Precisamos verificar:** dado adicional ou checagem. **Limitação:** o que a base não permite concluir.

## Rubrica: 10 pontos

|Critério|2 pontos|1 ponto|0 pontos|
|---|---|---|---|
|Qualidade dos dados|Auditoria e decisões registradas|Auditoria parcial|Filtros silenciosos ou inválidos ignorados|
|Resumos|Medidas corretas, unidades e n|Uma omissão relevante|Resultados inconsistentes|
|Gráficos|Dois gráficos adequados e legíveis|Um gráfico adequado ou eixos incompletos|Gráficos não respondem à pergunta|
|Investigação|Contexto, sensibilidade ou estratificação|Apenas sinalização|Exclusão ou conclusão sem fundamento|
|Reprodutibilidade e interpretação|Código executável, evidências e limites|Código ou limitações incompletos|Somente texto da LLM sem evidência|

## Gabarito de conferência

Consulte depois da tentativa: `analise_referencia.ipynb`. Ele inclui os dados incorporados e as saídas calculadas, podendo ser aberto sozinho.

- 62 linhas brutas; 1 duplicata exata de P012; P061 tem -40 e viola o contrato de pedidos concluídos sem estorno; 60 pedidos válidos.
- 6 entregas ausentes: 10%; 54 pares completos na correlação.
- Média 195,0167; mediana 158,5; desvio-padrão amostral 294,1993 reais.
- Q1=114,5; Q3=203,5; IQR=89; limites -19 e337. Somente P048 (2400) sinalizado.
- Sem o sinalizado, n=59, média157,6441, mediana156, desvio52,8957 reais. Cenário exploratório, não uma nova base definitiva.
- Medianas por canal: Orgânico113, Pago204; n=30 em cada grupo. Diferença não prova efeito causal do canal.
- Pearson≈-0,9592; Spearman≈-0,9634 em54 pares. A associação foi construída no gerador; não é evidência sobre consumidores.
- Sem comprovante, quantidade e contexto, a validade do pedido alto permanece inconclusiva.
