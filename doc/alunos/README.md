# **PAGSCHOOL DOC API • ALUNOS**


As sequintes API estão disponíveis para a parte de Alunos.

- Criação de aluno
- Atualização de dados do aluno
- Pesquisa de aluno



## CRIAÇÃO DE ALUNO  

A requisição a seguir adiciona um aluno novo na plataforma PagSchool:
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
  "dataNascimentoResponsavel":"1953-02-13",
  "generoResponsavel":"M",
  "telefoneCelularResponsavel":"91988244142",
  "cpfResponsavel":"06640044234",
  "nomeResponsavel":"dias",
  "alunoResponsavelFinanceiro":false
}

```
Segue a descrição dos campos:


| Atributo | Obrigatório | Descrição|
| --- | ----------- |----------- |
|cpf| -- | CPF do aluno, **Sim** somente para alunos que são o próprio responsável  financeiro <br>  **Formato**: somente números|
|telefoneCelular| **Sim** | Formato: somente números|
|telefoneFixo| não | Formato: somente números |
|nomeAluno| **Sim** | Limite de 255 caracteres|
|dataNascimento| **Sim** | Formato: AAAA-MM-DD|
|email| **Sim** | |
|genero| **Sim** | Valores aceitos: **M** ou **F**|
|cep| **Sim** | Formato: Somente números |
|logradouro| **Sim** | |
|enderecoComplemento| não |  |
|bairro| **Sim** |  |
|localidade| **Sim** |  |
|uf| **Sim** |  |
|numero| **Sim** |  |
|dataNascimentoResponsavel| não | Formato: AAAA-MM-DD |
|generoResponsavel| sim | Valores aceitos: **M** ou **F**  |
|telefoneCelularResponsavel| sim | Somento números, formato DDD+NÚMERO TELEFONE |
|cpfResponsavel| -- | **Obrigátorio** para alunos que não são os responsável financeiro |
|nomeResponsavel| -- | **Obrigátorio** para alunos que não são os responsável financeiro |
|alunoResponsavelFinanceiro| **Sim** | Valores aceitos: **true** ou **false**|


Exemplo de resposta da criação de aluno:

```JSON
{
    "possuiContratoCancelado": false,
    "telefoneCelularWhatsapp": false,
    "telefoneCelularResponsavelWhatsapp": false,
    "id": 59,
    "cpf": "32773015835",
    "telefoneCelular": "91988244142",
    "telefoneFixo": null,
    "nomeAluno": "wallace souza",
    "dataNascimento": "1984-05-30",
    "email": "naopossui@email.com",
    "genero": "M",
    "cep": "66813750",
    "logradouro": "Travessa N-5",
    "enderecoComplemento": null,
    "bairro": "Campina de Icoaraci (Icoaraci)",
    "localidade": "Belém",
    "uf": "PA",
    "numero": "357",
    "escola_id": 1,
    "status": "CURSANDO",
    "dataNascimentoResponsavel": "1953-02-13",
    "generoResponsavel": "M",
    "telefoneCelularResponsavel": "91988244142",
    "cpfResponsavel": "06640044234",
    "nomeResponsavel": "dias",
    "nacionalidade": "BR",
    "alunoResponsavelFinanceiro": false,
    "updated_at": "2021-08-28T01:33:38.334Z",
    "created_at": "2021-08-28T01:33:37.432Z"
}
```


## ATUALIZAÇÃO DE ALUNO

A requisição a seguir atualiza os dados de aluno na plataforma:

```
PUT - {{endpoint}}/api/aluno/update
```

Utilize o JSON de retorno da API da criação de aluno para atualizar os dados necessários.  

O atributo de nome **status** pode ser atualizar com os seguinte valores: CURSANDO, FORMADO



## PESQUISA DE ALUNOS

A requisição a seguir pesquisa na base de alunos cadastrados.

```
GET - {{endpoint}}/api/aluno/all
```

Em conjunto com a requisição anterior, os seguintes parametro de consulta são aceitos na requisição:

```
status - Status do aluno, valor padrão 'CURSANDO', valores aceitos CURSANDO,FORMADO
limit - Limite de resultados na consulta, valor padrão 50
offset - Número de resultados iniciais que devem ser desconsiderados da resposta, valor padrão 0 
filter - Nome a ser consultado, tanto no nome do aluno quanto no nome do responsável
cpf - CPF do aluno, deve ser informado os 11 digitos, caso contrário retornará vazio como resposta.
cpfResponsavel - CPF do responsável, deve ser informado os 11 digitos, caso contrário retornará vazio como resposta. Pode ser usado com o paramêtro 'cpf'.

```
Exemplo de requisição

```
GET - {{endpoint}}/api/aluno/all?status=CURSANDO&limit=50&offset=0&filter=
```

Exemplo de resultado da consulta:

```JSON
{
  "count": 18,
  "rows": [],
  "totalAlunosCadastrados": 18
}
```

Descrição da resposta:

```
count - total de alunos da consulta
rows - Array do tipo de JSON de Aluno
totalAlunosCadastrados - Total de alunos cadastrados na plataforma

```


Próximo passo: [Acessar api de Contratos](../contratos)
