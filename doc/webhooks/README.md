# **PAGSCHOOL DOC API • WEBHOOKS**

Os seguintes eventos estãos dipsoníveis para disparo de requisições:


- Criação de acordo [>](#criacao-acordo)
- Status de parcela atualizado [>](#status-parcela-atualizado)
- Alteração de tag de devedor [>](#alteracao-tag-devedor)



**ATENÇÃO**  
Para efetividade dos webhooks, acione o suporte da I9 recebíveis para cadastrar 
as urls que irão receber os eventos.  

Todas as requisições enviam um token no header 'x-webhook-token', cujo valor é gerado pela biblioteca [hashids](https://hashids.org/).   
A chave de validação é gerada pelo suporte da I9 e passada para a escola.


# Criação de acordo [ # ](#criacao-acordo) 

Método: POST  

Campo numeroContrato: Esse campo representa o número de contrato no sistema do cliente, para melhor integração, acione o suporte da I9 e informe o valor do contrato.

Exemplo de requisição JSON:

```JSON
{
  "event":"ACORDO_CRIADO",
  "data":{
    "numeroContrato":null,
    "cpf":"09575467345",
    "acordoId":643,
    "devedorId":12305,
    "parcelas": [
      {
        "parcelaId":1683,
        "numeroParcela": 1,
        "valor":140,
        "vencimento":"2022-04-01",
        "status":"AGUARDANDO_PAGAMENTO"
      }
    ]
  }
}
```


# Status de parcela atualizado [ # ](#status-parcela-atualizado) 

Método: POST  

Campo numeroContrato: Esse campo representa o número de contrato no sistema do cliente, para melhor integração, acione o suporte da I9 e informe o valor do contrato.

Exemplo de requisição JSON:

```JSON
{
  "event":"STATUS_PARCELA_ACORDO_ATUALIZADO",
  "data":{
    "numeroContrato":null,
    "cpf":"09575467345",
    "acordoId":643,
    "devedorId":12305,
    "parcela":{
      "parcelaId":1683,
      "numeroParcela": 1,
      "valor":140,
      "vencimento":"2022-04-01",
      "status":"AGUARDANDO_PAGAMENTO",//Valores aceitos: PAGO,AGUARDANDO_PAGAMENTO,VENCIDA
      "dataPagamento": "2022-04-01" //Valor preenchido somente quando o status for PAGO
    }
  }
}
```



# Alteração de tag de devedor [ # ](#alteracao-tag-devedor)

Método: POST  

Campo numeroContrato: Esse campo representa o número de contrato no sistema do cliente, para melhor integração, acione o suporte da I9 e informe o valor do contrato.


Exemplo de requisição JSON:

```JSON
{
  "event":"ALTERACAO_TAG_DEVEDOR",
  "data":{
    "numeroContrato":null,
    "cpf":"09575467345",
    "devedorId":12305,
    "tag":"POSSÍVEL CONTATO INVÁLIDO",
    "tagDescricao":"Refere-se ao contato inválido ou não existente. "
  }
}
```

