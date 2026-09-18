# Análise exploratória de pedidos

Notebook da atividade de laboratório sobre auditoria e análise exploratória de pedidos sintéticos.

## Arquivos

- `analise_pedidos.ipynb`: notebook com código, tabelas, gráficos e saídas executadas.
- `pedidos_sinteticos.csv`: dados sintéticos usados na atividade.
- `DICIONARIO.md`: campos, unidades e regras dos dados.
- `instrucao/laboratorio.md`: roteiro e critérios da atividade.
- `requirements.txt`: dependências Python.

## Site do professor

Material de apoio e instruções da atividade:

[Ciência de Dados](https://condebaba.github.io/CienciaDados/)

## Como executar

1. Crie e ative um ambiente virtual:

   **Windows (PowerShell):**

   ```powershell
   python -m venv .venv
   .venv\Scripts\Activate.ps1
   ```

   **Linux:**

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

2. Instale as dependências:

   ```bash
   pip install -r requirements.txt
   ```

3. Abra o notebook:

   ```bash
   jupyter notebook analise_pedidos.ipynb
   ```

   Também é possível abrir o arquivo diretamente no VS Code com a extensão Jupyter instalada.

Execute as células em ordem, a partir da célula de preparação. O notebook preserva o CSV bruto e trabalha com uma cópia lógica.

## Dados e interpretação

Os dados são sintéticos e servem para exploração e auditoria. A análise não permite inferência populacional nem conclusões causais. Ausentes em `entrega_dias` representam informação não registrada, e não zero.

## O que não versionar

O arquivo `.gitignore` exclui ambientes virtuais, caches do Python e checkpoints do Jupyter. Não envie a pasta `.venv/` para o repositório; cada integrante deve instalá-la no próprio ambiente a partir de `requirements.txt`.
