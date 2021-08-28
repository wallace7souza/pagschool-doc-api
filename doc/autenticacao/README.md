# **PAGSCHOOL DOC API • AUTENTICAÇÃO**

A autenticação da API se dá pela sequinte requisição: 

**POST** - <span style="color:e5e5e5">{{endpoint}}</span>/api/authenticate

Corpo requisição: 
```json
{
  "email":"seu_email@example.com",
  "password":"senha_ultra_secreta"
}
```

Para cadastro de usuário, informe um e-mail válido e uma senha para o suporte da inove(suporte@i9escola.com.br).

A respostas da requisição de autenticação se dá no formato **json** como a seguir:

```json
{
    "user": {
        "id": 1,
        "email": "seu_email@example.com",
        "username": "usuario",
        "language": null,
        "timezone": null,
        "firstName": "usuario",
        "lastName": null,
        "provider": "local",
        "codigoEscola": "0000",
        "codigoEscolaList": null,
        "cor": null,
        "skype": null,
        "whereby": null,
        "role": "CLIENTE",
        "status": "ENABLED",
        "created_at": "2020-10-27T17:00:17.000Z",
        "updated_at": "2020-10-27T17:00:17.000Z"
    },
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9...eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9"
}
```

Além dos dados relativos ao usuário logado, o atributo **token** é retornado. Com o valor do token, adicione ele no header
nas requisições de para as APIs de **aluno,contratos,parcelas e conta virtual.**

```code
Authorization: JWT eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9...eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9
```


Próximo passo: [Acessar api de Alunos](./alunos)
