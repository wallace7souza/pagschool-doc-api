# **PAGSCHOOL DOC API • CONTRATOS**


[comment]: <> (As sequintes API estão disponíveis para acesso aos contratos.  )

- Criação de contrato
- Atualização de contrato
- Contratos por aluno
- Excluir contrato

## CRIAÇÃO DE CONTRATO

A requisição a seguir adiciona um aluno novo na plataforma:
```
POST - {{endpoint}}/api/contrato/create
```
Exemplo de corpo da resquisição
```JSON
{
   "numeroContrato":"0001",
   "nomeCurso":"curso teste",
   "duracaoCurso":5,
   "valorParcela":100,
   "quantidadeParcelas":7,
   "diaProximosVencimentos":20,
   "vencimentoPrimeiraParcela":"2020-12-15",
   "descontoAdimplencia":null,
   "descontoAdimplenciaValorFixo":10.50,
   "aluno_id":1,
   "numeroParcelaInicial":1
}
```
Segue a descrição dos campos:


| Atributo | Obrigatório | Descrição|
| --- | ----------- |----------- |
|numeroContrato| não | Descrição livre de acordo com o tipo de contrato da escola |
|nomeCurso| não | Descrição livre de acordo com o tipo de contrato da escola |
|duracaoCurso| não | Duraçao do curso em meses |
|valorParcela| :heavy_check_mark: | Valor de cada parcela a ser paga |
|quantidadeParcelas| :heavy_check_mark: | Número total de parcelas  |
|diaProximosVencimentos| :heavy_check_mark: | Dia de vencimento  para as próximos parcelas  |
|vencimentoPrimeiraParcela| :heavy_check_mark: | Dia de vencimento  para as primeira parcela  |
|descontoAdimplencia| não | Porcentagem de desconto por adimplencia a ser aplicado as parcelas <br> Formato float.  |
|descontoAdimplenciaValorFixo| não | Valor fixo de desconto por adimplencia a ser aplicado as parcelas <br> Formato float. |
|aluno_id| :heavy_check_mark: | Id do aluno a qual será associado a criação do contrato |
|numeroParcelaInicial| não | Número inicial da parcela, valor padrão 1. Campo necessario para migrar contratos  em andamento, ex: um contrato já possui pago 3 parcelas de 6, o valor do campo será 4 e a quantidadeParcelas será 6, criando assim 3 parcelas a serem  geridas pela plataforma. |


Exemplo de resposta da criação de contrato:
```JSON
{
    "parcelasPagas": 0,
    "id": 106,
    "numeroContrato": "0001",
    "nomeCurso": "curso teste",
    "duracaoCurso": 5,
    "valorParcela": 100,
    "quantidadeParcelas": 7,
    "descontoAdimplencia": null,
    "descontoAdimplenciaValorFixo": 10,
    "aluno_id": 1,
    "criadopor_id": 2,
    "recebeMensagem": true,
    "recebeMensagemAntesVencimento": true,
    "recebeMensagemPosVencimento": true,
    "status": "ATIVO",
    "updated_at": "2021-08-28T12:39:32.938Z",
    "created_at": "2021-08-28T12:39:32.879Z",
    "proximaparcela_id": 513
}
```


## ATUALIZAÇÃO DE CONTRATO

A requisição a seguir atualiza os dados de contrato na plataforma:

```
PUT - {{endpoint}}/api/contrato/update
```

Utilize o JSON de retorno da API da criação de contrato para atualizar os dados necessários.

O seguintes atributos estão disponíveis para atualização a nível de api:

    numeroContrato, nomeCurso, duracaoCurso

Para **cancelamento** ou **exclusão** de contrato, entre em contato com a administração do sistema.


## CONTRATOS POR ALUNO

A requisição a seguir lista todos os contratos atrelado a um aluno:

```
GET - {{endpoint}}/api/contrato/by-aluno/:alunoId
```

Onde o parametro **:alunoId** é o id de um aluno cadastrado na plataforma.


Exemplo de resposta de contrato de aluno:
```JSON
[
  {
    "id": 3333445533,
    "valorParcela": 100,
    "quantidadeParcelas": 24,
    "numeroContrato": "E210703",
    "nomeCurso": "ATEND FARMACIA",
    "descontoAdimplencia": 0,
    "descontoAdimplenciaValorFixo": null,
    "parcelasPagas": 0,
    "proximaparcela_id": 267,
    "duracaoCurso": 24,
    "valorTotalContrato": null,
    "valorEntrada": null,
    "dataVencimentoEntrada": null,
    "status": "ATIVO",
    "recebeMensagem": true,
    "recebeMensagemAntesVencimento": true,
    "recebeMensagemPosVencimento": true,
    "quantidadeParcelasVencidas": 0,
    "dataCancelamento": null,
    "possuiParcela30DiasVencida": false,
    "created_at": "2021-07-20T20:29:35.000Z",
    "updated_at": "2021-07-20T20:29:36.000Z",
    "aluno_id": 38,
    "criadopor_id": 6,
    "atualizadopor_id": null,
    "parcelas": [
      {
        "diasVencida": 0,
        "diasUteisVencida": -1,
        "vencimentoFds": false,
        "id": 267,
        "valor": 100,
        "valorPago": 100,
        "taxas": 2.89,
        "valorDescontoAdimplencia": 0,
        "valorServicosI9": null,
        "numeroBoleto": "74891121152192852602507128531097187280000010000",
        "boletoUrl": null,
        "vencimento": "2021-08-30",
        "dataPagamento": "2021-08-27",
        "numeroParcela": 1,
        "status": "PAGO",
        "emissaoSicrediJson": "{\"linhaDigitavel\":\"74891121152192852602507128531097187280000010000\",\"codigoBanco\":\"748\",\"nomeBeneficiario\":\"I9 GESTAO DE RECEBIVEIS E COBR\",\"enderecoBeneficiario\":\"R. EMBAUTINGA, 363\",\"cpfCnpjBeneficiario\":\"31674043000186\",\"cooperativaBeneficiario\":\"2602\",\"postoBeneficiario\":\"07\",\"codigoBeneficiario\":\"12853\",\"dataDocumento\":\"2021-07-20\",\"seuNumero\":\"267\",\"especieDocumento\":\"K\",\"aceite\":\"N\",\"dataProcessamento\":\"2021-07-20\",\"nossoNumero\":211219285,\"especie\":\"REAL\",\"valorDocumento\":100,\"dataVencimento\":\"2021-08-30\",\"nomePagador\":\"VANESSA DOS SANTOS SILVA - E210703\",\"cpfCnpjPagador\":\"35146186820\",\"enderecoPagador\":\"RUA NELSON ALEXANDRE\",\"dataLimiteDesconto\":null,\"valorDesconto\":0,\"jurosMulta\":0.03,\"instrucao\":\"Pague em qualquer casa lotérica.\\rAPOS VENCIMENTO COBRAR MULTA DE    2.00 %.\\rAPOS VENCIMENTO COBRAR MORA DIARIA DE R$ 0.03.\\r\",\"informativo\":\"Fique atento à data de vencimento do boleto.\\r\",\"codigoBarra\":\"74891872800000100001121121928526020712853109\"}",
        "userId": null,
        "baixaManual": false,
        "descricao": null,
        "confirmacaoPagamentoJson": null,
        "nossoNumero": "211219285",
        "valorBoleto": 2.89,
        "valorRecebido": null,
        "dataBaixa": null,
        "dataGeracaoBoleto": null,
        "created_at": "2021-07-20T20:29:35.000Z",
        "updated_at": "2021-08-27T13:24:08.000Z",
        "contrato_id": 33,
        "criadopor_id": 6,
        "criadopor": {
          "id": 6,
          "firstname": "cliente"
        }
      }
    ]
  }
]

```


Próximo passo: [Acessar api de Parcelas](../parcelas)
