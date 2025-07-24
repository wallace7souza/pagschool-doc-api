# **PAGSCHOOL DOC API • PARCELAS**

As sequintes API estão disponíveis para acesso as parcelas.

- Criação de parcela
- Atualização de parcela
- Exclusão de parcela
- Geração de boleto de parcela
- Gerar PDF único de parcela
- Gerar PDF de todas as parcelas de um contrato
- Baixa manual de parcela




## CRIAÇÃO DE PARCELA

A requisição a seguir adiciona uma nova parcela ao contrato:

OBS: As parcelas originalmente são criadas juntamente do contrato. Esta requisição serve para criação individual de uma parcela em um contrato já criado.
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



Exemplo de resposta da criação de parcela:
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

OBS: A alteração só será permitida em parcelas ainda não pagas.

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

OBS: A Exclusão só poderá ocorrer em parcelas que não possuem ocorrências de cobranças, ou seja, recém criadas. Qualquer outra alteração, deve ser comunicada à gestão da PagSchool.

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

Onde **:parcelaId** é o id da parcela a ser gerado o boleto.

Em caso de sucesso, um JSON de parcela é retornado, com o atributo **nossoNumero** preenchido assim  
como o atributo **numeroBoleto**.


## GERAÇÃO DE PDF ÚNICO DE PARCELA

OBS: É necessário já possuir um boleto **GERADO** na parcela para que a url funcione. 

Para baixar o PDF, componha a URL da seguinte forma:
```
{{endpoint}}/api/parcelas-contrato/pdf/:parcelaId/:nossoNumero
```
Onde **:parcelaId** é o id da parcela e o **:nossoNumero** é o valor que retornou anteriormente quando gerou o boleto da parcela.


## GERAÇÃO DE PDF de todas as parcelas

Faça uma requisição com o id do contrato da seguinte forma:

```
GET - {{endpoint}}/api/contrato/gerar-carne-boletos/:contratoId
```
Onde **:contratoId** é o id do contrato já criado que deseja coletar todos os boletos.

Exemplo de resposta:
```JSON
{
    "file": "carne-aluno-teste.pdf"
}
```

A requisição retorna o nome do arquivo. Com este nome, baixe o PDF pela seguinte URL:

{{endpoint}}/api/contrato/boletos-pdf/<RANDO_INTEGER>/carne-aluno-teste.pdf

<RANDO_INTEGER> é qualquer número inteiro, somente para evitar cache do navegador.


## BAIXA MANUAL DE PARCELA

A requisição a seguir realiza baixa manual de uma parcela na plataforma:
```
POST - {{endpoint}}/api/parcelas-contrato/gerar-baixa-parcela/:parcelaId
```
Onde **:parcelaId** é o id da parcela a ser baixada.

Exemplo de corpo da resquisição
```JSON
{
  "valorPago":100,
  "dataPagamento":"2021-06-20"
}
```
Descrição dos atributos da requisição:

    valorPago: Valor em reais, referente ao valor pago, formato float.
    dataPagamento: Data da realização da baixa de parcela. (OBS: Sempre fornecer a data do dia em que está baixando). 



Próximo passo: [Acessar api de cotna virtual](../conta-virtual)
