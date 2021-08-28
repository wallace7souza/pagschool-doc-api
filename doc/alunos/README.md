# **PAGSCHOOL DOC API • ALUNOS**


As sequintes API estão disponíveis para acesso aos alunos.

- Criação de aluno
- Atualização de aluno 
- Pesquisa de alunos



## CRIAÇÃO DE ALUNO  

A requisição a seguir adiciona um aluno novo na plataforma:
```
POST - {{endpoint}}/api/aluno/new
```
Exemplo de corpo da resquisição
```JSON

{
  "cpf":"10994453027",
  "telefoneCelular":"91988244142",
  "telefoneFixo":null,
  "nomeAluno":"wallace souza",
  "dataNascimento":"1984-05-30",
  "email":"naopossui@email.com",
  "genero":"M",
  "cep":"66813750",
  "logradouro":"Travessa N-5",
  "enderecoComplemento":null,
  "bairro":"Campina de Icoaraci (Icoaraci)",
  "localidade":"Belém",
  "uf":"PA",
  "numero":"357",
  "status":"CURSANDO",
  "dataNascimentoResponsavel":"1953-02-13",
  "generoResponsavel":"M",
  "telefoneCelularResponsavel":"91988244142",
  "cpfResponsavel":"06640044234",
  "nomeResponsavel":"dias",
  "nacionalidade":"BR",
  "alunoResponsavelFinanceiro":false
}

```
Segue a descrição dos campos :heavy_check_mark:

:joy:

| Atributo | Obrigatório | Descrição|
| --- | ----------- |----------- |
|cpf| -- | **Obrigatório** somente para alunos que são o próprio responsável  financeiro <br>  **Formato**: somente números|
|telefoneCelular| não | Formato: somente números|
|telefoneFixo| não | Formato: somente números |
|nomeAluno| <span style="color:green">sim</span>     | Limite de 255 caracters|
|dataNascimento| não | Formato: AAAA-MM-DD|
|email| não | |
|genero| :heavy_check_mark: | descricao|
|cep| sim | descricao|
|logradouro| sim | descricao|
|enderecoComplemento| sim | descricao|
|bairro| sim | descricao|
|localidade| sim | descricao|
|uf| sim | descricao|
|numero| sim | descricao|
|status| sim | descricao|
|dataNascimentoResponsavel| sim | descricao|
|generoResponsavel| sim | descricao|
|telefoneCelularResponsavel| sim | descricao|
|cpfResponsavel| sim | descricao|
|nomeResponsavel| sim | descricao|
|nacionalidade| sim | descricao|
|alunoResponsavelFinanceiro| sim | descricao|

