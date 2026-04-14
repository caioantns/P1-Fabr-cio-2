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


<img width="630" alt="print1" src="https://github.com/user-attachments/assets/4b2720c2-dca3-4e2a-9bd6-9287a49eb025" />




2. Consultas Realizadas

2.1- Buscar todos os alunos


<img width="501" height="882" alt="Mostrar todos os alunos" src="https://github.com/user-attachments/assets/3d3e0310-d271-4120-9b04-a4b74011b708" />



2.2- Buscar alunos do curso "ADS"
db.alunos.find({ curso: "ADS" });


<img width="462" height="405" alt="Listar todos os alunos em ADS" src="https://github.com/user-attachments/assets/08aee552-4051-4052-83a2-0f6ee202feb8" />


2.3- Buscar alunos com idade maior que 21
db.alunos.find({ idade: { $gt: 21 } });


<img width="398" height="405" alt="Listar todos os alunos com mais de 21 anos" src="https://github.com/user-attachments/assets/a2bd4e23-7340-4347-8072-8aecc79e1f8b" />


2.4- Atualizar a idade de um aluno
db.alunos.updateOne({ nome: "João Silva" }, { $set: { idade: 21 } });


<img width="514" height="176" alt="Atualizar a idade de um aluno" src="https://github.com/user-attachments/assets/cf37df07-5726-4b16-9f82-4f997481fa42" />


2.5- Adicionar uma nova nota a um aluno
db.alunos.updateOne({ nome: "Ana Souza" }, { $push: { notas: 10 } });


<img width="335" height="118" alt="Deletar um aluno da lista" src="https://github.com/user-attachments/assets/780311d8-1241-446a-b305-b586cc799a10" />


2.6- Remover um aluno
db.alunos.deleteOne({ nome: "Carlos Lima" });


<img width="574" height="181" alt="Alterar as notas de um aluno" src="https://github.com/user-attachments/assets/a43d85c4-38d0-4af8-b568-533a802af9d7" />


2.7- Média de notas por aluno
db.alunos.aggregate([
  {
    $project: {
      nome: 1,
      media: { $avg: "$notas" }
    }
  }
]);


<img width="437" height="582" alt="Mostrar as médias dos alunos" src="https://github.com/user-attachments/assets/59b1b573-facf-4070-b631-dcdb4de09550" />


2.8- Quantidade de alunos por curso
db.alunos.aggregate([
  {
    $group: {
      _id: "$curso",
      total: { $sum: 1 }
    }
  }
]);


<img width="417" height="424" alt="Quantidade de aluno por curso" src="https://github.com/user-attachments/assets/a6d19d9b-be2e-464e-9f6e-e46fc7d9e78b" />

