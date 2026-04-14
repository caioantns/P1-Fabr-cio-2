# P1 - Banco de Dados NoSQL (MongoDB + Docker) 🎓

**Aluno:** Caio [Seu Sobrenome]  
**Curso:** Engenharia de Software - 5º Período  
**Local:** Maricá, RJ

Este repositório contém a resolução da avaliação prática de Banco de Dados, focada em operações CRUD e agregações utilizando o terminal `mongosh` dentro de um ambiente Docker.

---

## 🚀 Execução da Prova

### 1. Inserção de Dados
Os dados foram inseridos conforme o modelo proposto, utilizando um conjunto de 5 alunos.

```javascript
db.alunos.insertMany([
  {
    "nome": "Yuji Itadori",
    "idade": 16,
    "curso": "ADS",
    "notas": [7, 8, 9],
    "endereco": { "cidade": "Maricá", "estado": "RJ" }
  },
  {
    "nome": "Satoru Gojo",
    "idade": 28,
    "curso": "Engenharia de Software",
    "notas": [8, 9, 10],
    "endereco": { "cidade": "Niterói", "estado": "RJ" }
  },
  {
    "nome": "Megumi Fushiguro",
    "idade": 16,
    "curso": "ADS",
    "notas": [6, 5, 7],
    "endereco": { "cidade": "Rio de Janeiro", "estado": "RJ" }
  },
  {
    "nome": "Nobara Kugisaki",
    "idade": 16,
    "curso": "Sistemas",
    "notas": [9, 9, 8],
    "endereco": { "cidade": "Maricá", "estado": "RJ" }
  },
  {
    "nome": "Suguru Geto",
    "idade": 27,
    "curso": "Engenharia de Software",
    "notas": [10, 9, 9],
    "endereco": { "cidade": "São Gonçalo", "estado": "RJ" }
  }
]);


2. Consultas Realizadas

2.1- Buscar todos os alunos
db.alunos.find().toArray();


2.2- Buscar alunos do curso "ADS"
db.alunos.find({ curso: "ADS" });


2.3- Buscar alunos com idade maior que 21
db.alunos.find({ idade: { $gt: 21 } });


2.4- Atualizar a idade de um aluno
db.alunos.updateOne({ nome: "João Silva" }, { $set: { idade: 21 } });


2.5- Adicionar uma nova nota a um aluno
db.alunos.updateOne({ nome: "Ana Souza" }, { $push: { notas: 10 } });


2.6- Remover um aluno
db.alunos.deleteOne({ nome: "Carlos Lima" });


2.7- Média de notas por aluno
db.alunos.aggregate([
  {
    $project: {
      nome: 1,
      media: { $avg: "$notas" }
    }
  }
]);


2.8- Quantidade de alunos por curso
db.alunos.aggregate([
  {
    $group: {
      _id: "$curso",
      total: { $sum: 1 }
    }
  }
]);