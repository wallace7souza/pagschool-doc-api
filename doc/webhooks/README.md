# **PAGSCHOOL DOC API • WEBHOOKS**

Os seguintes eventos estãos dipsoníveis para disparo de requisições:

- Atualização de Status de Parcela de contrato


**ATENÇÃO**  
Para efetividade dos webhooks, acione o suporte da I9 recebíveis para cadastrar a url que irá receber os eventos.  



# Status de parcela atualizado [ # ](#status-parcela-atualizado) 

Método: POST  

Exemplo de requisição JSON:

```JSON
{
    "id": 1242236, // id da parcela
    "valor": 35,
    "valorPago": 20,
    "numeroBoleto": "74891160745953052602507128531063696770000003500",
    "vencimento": "2024-04-05",
    "dataPagamento": "2024-04-05",
    "nossoNumero": "607595305",
    "contrato_id": 60011,
}
```


