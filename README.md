[![Latest Stable Version](https://poser.pugx.org/andrebian/pag_seguro/v/stable.png)](https://packagist.org/packages/andrebian/pag_seguro) [![Total Downloads](https://poser.pugx.org/andrebian/pag_seguro/downloads.png)](https://packagist.org/packages/andrebian/pag_seguro) [![Latest Unstable Version](https://poser.pugx.org/andrebian/pag_seguro/v/unstable.png)](https://packagist.org/packages/andrebian/pag_seguro) [![License](https://poser.pugx.org/andrebian/pag_seguro/license.png)](https://packagist.org/packages/andrebian/pag_seguro)
[![githalytics.com alpha](https://cruel-carlota.pagodabox.com/8d4bc51766116b27f682121865660505 "githalytics.com")](http://githalytics.com/andrebian/cake-plugin-pagseguro)

# PAGSEGURO PLUGIN
_v 2.0.3_


Facilita a integração de pagamentos via PagSeguro em aplicações desenvolvidas com base no CakePHP 2.x.
O plugin realiza apenas interfaceamento para a API de pagamentos do PagSeguro, com
isso nem o plugin nem o PagSeguro podem ser responsabilizados por uso em desconformidade à documentação fornecida pelo PagSeguro <https://pagseguro.uol.com.br/v2/guia-de-integracao/visao-geral.html> assim como valores fornecidos. A responsabilidade das corretas informações ao PagSeguro são estritamente do programador que criará a requisição no fechamento do carrinho de compras.

____________________

## INSTALAÇÃO

Composer
---------------
```json
{
    "require": {
        "andrebian/pag_seguro": "dev-master"
    }
}
```
Ou se preferir uma versão em específico:

```json
{
    "require": {
        "andrebian/pag_seguro": "2.0.0"
    }
}
```

##Atenção
> Não é mais fornecido suporte para download direto ou utilização como submodulo. Por depender da API oficial do PagSeguro a instalação faz-se de forma correta através do composer. Se quiser fazer desta forma (clone, zip ou submodulo) faça, mas não prestarei suporte pois o único meio que satisfaz todas as dependências é o indicado acima.

_________________________

## CONFIGURAÇÕES


### Carregando o plugin

No arquivo `bootstrap.php` adicione o suporte ao plugin:
`CakePlugin::load('PagSeguro');` ou `CakePlugin::loadAll();`


### Credenciais

Você deve possuir uma conta no PagSeguro pois precisará setar as credenciais,
estas credenciais são compostas pelo seu email e o token que deve ser configurado na seção de integração
junto ao PagSeguro.

Tal configuração pode ser feita de duas formas, via `bootstrap` ou no controller desejado.

Arquivo bootstrap
```php
Configure::write('PagSeguro', array(
    'email' => 'seu-email-cadastrado@pagseguro',
    'token' => 'seu-token',
    'isSandbox' => true, // true|false
));
```        


Controller qualquer onde será montada a finalização da compra
```php
$this->carrinho->defineCredenciais('email cadastrado', 'token gerado');
```


### Carregando o componente


Agora que você já configurou suas credenciais deve definir no `AppController` ou no controller
que o componente será utilizado

```php
public $components = array('PagSeguro.PagSeguro', 'PagSeguro.Checkout');
```


Caso já possua mais componentes faça-o da seguinte forma

```php
public $components = array('Outros componentes', 'PagSeguro.PagSeguro', 'PagSeguro.Checkout');
```


**A definição do `'PagSeguro.PagSeguro'` NÃO deve ser ignorada.**


## UTILIZAÇÃO


* Requisição de pagamento: Leia o arquivo [REQUISICAO_PAGAMENTO][1]
* Retorno de requisição de pagamento: Leia o arquivo [CONSULTA][2]
* Consulta por código: Leia o arquivo [CONSULTA][3]
* Consulta por perído: Leia o arquivo [CONSULTA][4]
* Consulta por transações abandonadas: Leia o arquivo [CONSULTA][5]
* Notificações: Leia o arquivo [NOTIFICACAO][6]

______________


##TODO

* Testes


##PROBLEMAS

Reporte-os por aqui https://github.com/andrebian/cake-plugin-pagseguro/issues?state=open

##CONTRIBUIDORES

* Marcelo Siqueira - https://github.com/marcelosiqueira


##ATENÇÃO
Muitos desenvolvedores utilizaram meu email pessoal que estava nos exemplos para realizar compras, peço humildemente que por favor, use SEU email para realizar os testes de compra, já ajudei com o plugin não posso ajudar verificando emails e dando reports.

Muito agradecido.


  [1]: https://github.com/andrebian/cake-plugin-pagseguro/blob/master/REQUISICAO_PAGAMENTO.md
  [2]: https://github.com/andrebian/cake-plugin-pagseguro/blob/master/CONSULTA.md
  [3]: https://github.com/andrebian/cake-plugin-pagseguro/blob/master/CONSULTA.md
  [4]: https://github.com/andrebian/cake-plugin-pagseguro/blob/master/CONSULTA.md
  [5]: https://github.com/andrebian/cake-plugin-pagseguro/blob/master/CONSULTA.md
  [6]: https://github.com/andrebian/cake-plugin-pagseguro/blob/master/NOTIFICACAO.md
