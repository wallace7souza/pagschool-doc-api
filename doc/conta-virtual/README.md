# **PAGSCHOOL DOC API • CONTA VIRTUAL**


As sequintes API estão disponíveis para acesso aos detalhes de conta virtual.

- Informações da conta virutal
- Solicitação de saque da conta virtual



## INFORMAÇÕES  DA CONTA VIRTUAL

A requisição a seguir retorna os dados referente a sua conta virtual:
```
GET - {{endpoint}}/api/conta-virtual/account-info/:codigoEscola
```

Onde **:codigoEscola** é um valor criado pela i9 referente ao seu cadastro. 

Exemplo de resposta da resquisição
```JSON
{
  "_id":"6101898c16b893c4499820de",
  "codigo":"6008",
  "saldo":2596.16,
  "saldoAcompensar":607.51,
  "saldoADebitar":0,
  "saquesDisponiveis":2,
  "valorSaqueExtra":2.89,
  "saquesDisponiveisEscola":4,
  "valorSaqueExtraEscola":2.89,
  "valorBoletoPago":2.89,
  "pagaBoletoAcordo":true,
  "habilitaServicosI9":false,
  "valorServicosI9":1.99,
  "contasBancarias":[
    {
      "nomeBanco":"0XX - Banco AAAA",
      "agencia":"0393",
      "numeroConta":"140-4",
      "nomeTitular":"Mnha escola ",
      "cpfcnpj":"032.898.303-90",
      "contaPadrao":true
    }
  ]
}
```


## SOLICITAÇÃO DE SAQUE DA CONTA VIRTUAL

A requisição a seguir retorna os dados referente a sua conta virtual:
```
POST - {{endpoint}}/api/conta-virtual/solicitar-saque
```

Exemplo de corpo da resquisição
```JSON
{
  "valor": 100.0
}
```

Onde **valor** é em reais no formato float.
