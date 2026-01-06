📡 REST API — Conceitos Fundamentais e Consumo com Python

API do exemplo de faturamento desenvolida e disponibilizada no endpoint https://41e64eff-1a89-4de1-8eec-a0b1787d6dd2-00-1ti5kr0inb3cr.riker.replit.dev/

Este repositório reúne os conceitos essenciais sobre APIs REST, utilizando exemplos práticos e didáticos inspirados na API do Instagram, com foco no entendimento de requisições HTTP, JSON, CRUD e consumo de APIs em Python.

O descritivo desse README é ideal para quem está iniciando no tema ou deseja consolidar os fundamentos antes de avançar para frameworks como Flask ou FastAPI.

🧠 O que é uma API?

API (Application Programming Interface) é uma interface que permite a comunicação entre sistemas diferentes, sem a necessidade de interface gráfica.

👉 Em termos simples:

Um sistema faz um pedido

Outro sistema responde com dados

A comunicação ocorre por requisições HTTP

Os dados normalmente vêm em JSON

📌 Esse tipo de estrutura é exatamente o que recebemos ao consumir uma API.

🔁 Como pedir informações para uma API?

A comunicação ocorre por meio dos protocolos HTTP, usando métodos específicos.

📌 Principais métodos HTTP
Método	Ação	Conceito
GET	Ler	Buscar informações
POST	Criar	Criar novos registros
PUT / PATCH	Atualizar	Atualizar registros
DELETE	Deletar	Remover registros
🗂️ CRUD e sua relação com APIs

CRUD representa as operações básicas de um banco de dados:

CRUD	Método HTTP
Create	POST
Read	GET
Update	PUT / PATCH
Delete	DELETE
🐍 Consumindo APIs com Python

Utilizamos a biblioteca requests para realizar requisições HTTP.

🔧 Instalação
pip install requests

🔹 Exemplo 1 — Buscar todos os usuários
import requests

response = requests.get("api.instagram.com/usuarios")
print(response.json())


🔹 Retorno esperado:

{
  "ID254": "franciscoccarneiro",
  "ID357": "fulanodetal",
  "ID222": "siclanodetal"
}

🔹 Exemplo 2 — Buscar informações de um usuário específico
requests.get("api.instagram.com/usuarios/franciscoccarneiro")


🔹 Retorno:

{
  "ID254": {
    "nome": "Francisco",
    "idade": 43,
    "amigos": ["ID255", "ID256", "ID302"],
    "foto_perfil": "francisco.png"
  }
}

🔹 Exemplo 3 — Criar um post (POST)
requests.post(
    "api.instagram.com/usuarios/franciscoccarneiro/post",
    data={
        "foto": "francisco2.png",
        "titulo": "teste",
        "descricao": "teste aqui"
    }
)


🔹 Retorno:

{
  "status": "sucesso"
}

🔹 Exemplo 4 — Buscar um post específico
requests.get("api.instagram.com/usuarios/franciscoccarneiro/post/5")

🔹 Exemplo 5 — Atualizar um post (PATCH)
requests.patch(
    "api.instagram.com/usuarios/franciscoccarneiro/post/5",
    data={"titulo": "aleatório"}
)

🔐 Segurança em APIs

APIs definem:

O que pode ser acessado

Quem pode acessar

Quais ações são permitidas

📌 Isso garante:

Proteção dos dados

Padronização

Facilidade de integração com aplicativos, sites e outros sistemas


No exemplo prático eu criei uma api para integrar APIs com bancos de dados

📚 Tecnologias abordadas

HTTP

JSON

Python

Biblioteca requests

Conceitos REST

CRUD

🧑‍🏫 Objetivo do repositório

Este repositório tem como objetivo servir como material de apoio de mentoria, reforçando a base conceitual necessária para trabalhar com integrações, automações, engenharia de dados e ciência de dados.
