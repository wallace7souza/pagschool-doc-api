# **PAGSCHOOL DOC API • PARCELAS**

As sequintes API estão disponíveis para acesso as parcelas.

- Criação de parcela
- Atualização de parcela
- Exclusão de parcela
- Geração de boleto de parcela
- Baixa manual de parcela



## CRIAÇÃO DE CONTRATO

A requisição a seguir adiciona um aluno novo na plataforma:
```
POST - {{endpoint}}/api/parcelas-contrato/create
```
Exemplo de corpo da resquisição
```JSON
{
   "valor":100,
   "descricao":"descricao",
   "vencimento":"2021-06-20",
   "numeroParcela":7,
   "contrato_id":1
}
```

Segue a descrição dos campos:


| Atributo | Obrigatório | Descrição|
| --- | ----------- |----------- |
|valor| :heavy_check_mark: | Valor em reais da parcela, formato float |
|descricao| não | Descrição ou motivo da criação da parcela |
|vencimento| :heavy_check_mark: | Data de vencimento da parcela. |
|contrato_id| :heavy_check_mark: | Id do contrato a qual pertence a parcela. |



Exemplo de resposta da criação de contrato:
```JSON
{
    "diasVencida": 0,
    "diasUteisVencida": 36,
    "vencimentoFds": false,
    "baixaManual": false,
    "valorBoleto": 2.89,
    "id": 520,
    "valor": 100,
    "descricao": "descricao",
    "vencimento": "2021-10-20",
    "numeroParcela": 7,
    "status": "AGUARDANDO_PAGAMENTO",
    "contrato_id": 1,
    "criadopor_id": 2,
    "userId": 2,
    "updated_at": "2021-08-28T14:17:56.160Z",
    "created_at": "2021-08-28T14:17:56.160Z"
}
```



## ATUALIZAÇÃO DE PARCELA

A requisição a seguir atualiza uma parcela na plataforma:
```
PUT - {{endpoint}}/api/parcelas-contrato/update
```

Exemplo de corpo da resquisição
```JSON
{
  "id":5,
  "valor":100.5,
  "vencimento":"2021-10-08",
  "numeroParcela":5
}
```


## EXCLUSÃO DE PARCELA

A requisição a seguir excluir uma parcela na plataforma:
```
DELETE - {{endpoint}}/api/parcelas-contrato/delete/:parcelaId
```

Onde **:parcelaId** é o id da parcela a ser excluída.

Em caso de sucesso, a requisição retorna o seguinte json
```JSON
{"message":"ok"}
```

## GERAÇÃO DE BOLETO DE PARCELA

A requisição a seguir gera um boleto para a uma parcela na plataforma:
```
POST - {{endpoint}}/api/parcelas-contrato/gerar-boleto-parcela/:parcelaId
```

Onde **:parcelaId** é o id da parcela a ser excluída.

Em caso de sucesso, um JSON de parcela é retornado, com o atributo **nossoNumero** preenchido assim  
como o atributo **numeroBoleto**.

Para baixar o pdf faça uma requisição para a seguinte url
```
{{endpooint}}/api/parcelas-contrato/pdf/:parcelaId/:nossoNumero
```



## BAIXA MANUAL DE PARCELA

A requisição a seguir realiza baixa manual de uma parcela na plataforma:

Onde **:parcelaId** é o id da parcela a ser excluída.

Exemplo de corpo da resquisição
```JSON
{
  "valorPago":100,
  "dataPagamento":"2021-06-20"
}
```
Descrição dos atributos da requisição:

    valorPago: Valor em reais, referente ao valor pago, formato float.
    dataPagamento: Data da realização da baixa de parcela.



Próximo passo: [Acessar api de cotna virtual](../conta-virtual)
