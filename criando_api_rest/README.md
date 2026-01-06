📊 API de Vendas com Flask

Esta API REST foi desenvolvida em Python utilizando Flask com o objetivo de disponibilizar informações de faturamento e vendas por produto a partir de uma planilha Excel.

O projeto demonstra, de forma prática, como:

Criar endpoints REST

Ler dados com pandas

Agregar informações

Retornar respostas em formato JSON

🚀 API publicada

A API está publicada e em funcionamento, podendo ser acessada em:

🔗 URL base:

https://41e64eff-1a89-4de1-8eec-a0b1787d6dd2-00-1ti5kr0inb3cr.riker.replit.dev/

🧠 Visão geral do projeto

A aplicação lê um arquivo Excel chamado Vendas - Dez.xlsx

A base contém, entre outras colunas:

Produto

Valor Final

A API processa esses dados e expõe:

Faturamento total

Vendas agregadas por produto

Faturamento de um produto específico

🧱 Tecnologias utilizadas

Python

Flask

Pandas

Excel como fonte de dados

API REST

JSON

📂 Estrutura lógica do projeto
app.py
Vendas - Dez.xlsx

🔗 Endpoints disponíveis
🔹 1. Faturamento total

Endpoint

GET /


Descrição
Retorna o faturamento total somando a coluna Valor Final da planilha.

Exemplo de resposta

{
  "faturamento": 125430.75
}

🔹 2. Vendas agrupadas por produto

Endpoint

GET /vendas/produtos


Descrição
Retorna o faturamento total agrupado por produto.

Exemplo de resposta

{
  "Valor Final": {
    "Notebook": 45000,
    "Monitor": 32000,
    "Mouse": 8000
  }
}

🔹 3. Faturamento de um produto específico

Endpoint

GET /vendas/produtos/<produto>


📌 Substitua <produto> pelo nome do produto exatamente como está na planilha.

Exemplo

GET /vendas/produtos/Notebook


Resposta

{
  "Valor Final": 45000
}


🔸 Caso o produto não exista:

{
  "ProdutoX": "Inexistente"
}

🐍 Código principal da aplicação
from flask import Flask
import pandas as pd

app = Flask(__name__)
tabela = pd.read_excel("Vendas - Dez.xlsx")

@app.route("/")
def fat():
    faturamento = float(tabela["Valor Final"].sum())
    return {"faturamento": faturamento}

@app.route("/vendas/produtos")
def vendas_produtos():
    tabela_vendas_produtos = tabela[["Produto", "Valor Final"]].groupby("Produto").sum()
    return tabela_vendas_produtos.to_dict()

@app.route("/vendas/produtos/<produto>")
def fat_produto(produto):
    tabela_vendas_produtos = tabela[["Produto", "Valor Final"]].groupby("Produto").sum()
    if produto in tabela_vendas_produtos.index:
        return tabela_vendas_produtos.loc[produto].to_dict()
    else:
        return {produto: "Inexistente"}

app.run()

▶️ Como executar localmente
1️⃣ Instalar dependências
pip install flask pandas openpyxl

2️⃣ Executar a aplicação
python app.py

3️⃣ Acessar no navegador
http://127.0.0.1:5000/
