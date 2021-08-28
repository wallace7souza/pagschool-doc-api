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
|cpf| -- | CPF do aluno, **Obrigatório** somente para alunos que são o próprio responsável  financeiro <br>  **Formato**: somente números|
|telefoneCelular| não | Formato: somente números|
|telefoneFixo| não | Formato: somente números |
|nomeAluno| :heavy_check_mark:     | Limite de 255 caracteres|
|dataNascimento| não | Formato: AAAA-MM-DD|
|email| não | |
|genero| não | Valores aceitos: **M** ou **F**|
|cep| não | Formato: Somente números |
|logradouro| não | |
|enderecoComplemento| não |  |
|bairro| não |  |
|localidade| não |  |
|uf| não |  |
|numero| não |  |
|dataNascimentoResponsavel| não | Formato: AAAA-MM-DD |
|generoResponsavel| sim | Valores aceitos: **M** ou **F**  |
|telefoneCelularResponsavel| sim | Somento números, formato DDD+NÚMERO TELEFONE |
|cpfResponsavel| -- | **Obrigátorio** para alunos que não são os responsável financeiro |
|nomeResponsavel| -- | **Obrigátorio** para alunos que não são os responsável financeiro |
|alunoResponsavelFinanceiro| :heavy_check_mark: | Valores aceitos: **true** ou **false**|


Apesar de alguns campos não serem obrigatórios 
