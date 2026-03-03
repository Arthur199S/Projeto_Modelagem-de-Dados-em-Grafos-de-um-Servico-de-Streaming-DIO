# 🎬 Modelagem de Dados em Grafos — Serviço de Streaming

<img width="993" height="811" alt="bloom-visualisation" src="https://github.com/user-attachments/assets/3fdcef97-b684-4cf2-b2e8-acb32c8dfff5" />

## 📌 Descrição

Este projeto implementa um pequeno **grafo de conhecimento** para um serviço de streaming utilizando **Neo4j** e **Cypher**.  

O objetivo é modelar usuários, filmes e séries, bem como suas relações com atores, diretores e gêneros, permitindo consultas eficientes e recomendações baseadas em conexões.

---

## 🧠 Modelo de Dados

### 🔹 Nós (Entidades)

- **User**
- **Movie**
- **Series**
- **Genre**
- **Actor**
- **Director**

---

### 🔹 Relacionamentos

- `(:User)-[:WATCHED {rating}]->(:Movie | :Series)`
- `(:Actor)-[:ACTED_IN]->(:Movie | :Series)`
- `(:Director)-[:DIRECTED]->(:Movie | :Series)`
- `(:Movie | :Series)-[:IN_GENRE]->(:Genre)`

---

## 📊 Estrutura do Grafo

Exemplo de conexões:
(User)-[:WATCHED {rating: 9}]->(Movie)
(Actor)-[:ACTED_IN]->(Movie)
(Director)-[:DIRECTED]->(Movie)
(Movie)-[:IN_GENRE]->(Genre)


O relacionamento `WATCHED` contém a propriedade:

- `rating` → avaliação do usuário (ex: 1 a 10)

---

## 🛠 Tecnologias Utilizadas

- **Neo4j**
- **Cypher Query Language**

---

## 🔎 Exemplos de Consultas

### Ver avaliações de usuários

MATCH (u:User)-[w:WATCHED]->(m)
RETURN u.name, m.title, w.rating;

### Buscar filmes por gênero

MATCH (m:Movie)-[:IN_GENRE]->(g:Genre {name:"Ficção Científica"})
RETURN m.title;
### Buscar atores de um filme

MATCH (a:Actor)-[:ACTED_IN]->(m:Movie {title:"Interestelar"})
RETURN a.name;

### 🎯 Objetivo Acadêmico

Este projeto demonstra:

Modelagem orientada a grafos

Representação de relacionamentos complexos

Uso de propriedades em relacionamentos

Consultas eficientes baseadas em conexões

### 🚀 Possíveis Expansões

Sistema de recomendação baseado em similaridade

Peso em gêneros mais assistidos

Análise de popularidade por ator/diretor

Integração com API externa

### 📌 Conclusão

A modelagem em grafos permite representar de forma natural as conexões entre usuários e conteúdos, facilitando consultas complexas e análises relacionais em serviços de streaming.
