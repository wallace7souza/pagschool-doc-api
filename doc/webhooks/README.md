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

OBS: Segue abaixo um exemplo de página em .php para recebimento dos dados enviados pelo Webhook. A adaptação deve ocorrer conforme seu ambiente.


```JSON
<?php
header("Access-Control-Allow-Origin: *");
header('Cache-Control: no-cache, must-revalidate'); 
header("Content-Type: text/plain; charset=UTF-8");
header("HTTP/1.1 200 OK");
$dados = file_get_contents("php://input");

//DECODE OS DADOS
$dados_decode = json_decode($dados);

if(is_numeric($dados_decode->id) && !empty($dados_decode->id)){
    //INSTANCIO A CONEXÃO E AUTOLOAD
    require_once('../conexao.php');
    require_once('autoload.php');
    
    //CLASS
    $Banco = new escola\Bancos($con, 'Pagschool');
    $Parcela = new financeiro\Parcelas($con);
    
    //VERIFICA SE O PAGSCHOOL TA ATIVO
    if($Banco->statusPagSchool === '1'){
        $baixa = $Parcela->DarBaixa($dados_decode->id, 'PAGO', $dados_decode->dataPagamento, $dados_decode->valorPago, 'Baixa automática', 'DINHEIRO');
    }

}else{
    http_response_code(401);
    exit;
}

```
