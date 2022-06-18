# glpi-uspoauth
Gambiarra para fazer o GLPI autenticar no USP oAuth. Um dia vira plugin

**Testado na versão 9.5.4 à 9.5.7 do GLPI**

**Testado na versão 10.0.0** vide arquivo glpi10.rar

&nbsp;

## Setup Inicial

Para usar a autenticação do USP oAuth com o GLPI faça o seguinte:

- Cadastrar uma entrada no USP oAuth

- Entrar na pasta do GLPI e clonar o projeto

```
git clone git@github.com:stifdrp/glpi-uspoauth.git
```
 
- Inserir no index.php do GLPI, o código abaixo depois do botão de login
```php 
require_once ('glpi-uspoauth/botao-login.php');
```

![Código inserido](https://github.com/stifdrp/readme-images/blob/main/insert-code-glpi-uspoauth.png?raw=true)


- Criar uma cópia do config_example.php para config.php e setar as variáveis do seu ambiente
```php
$url_app = 'A URL DA SUA APLICACAO';
$consumer_key = 'SEU CONSUMER KEY';
$consumer_secret = 'SEU CONSUMER SECRET';
$callback_id = 'SEU CALLBACK ID';

//configuracoes do sistema
$unidade = "SIGLA DA SUA UNIDADE NO RETORNO DO OAUTH";
$passwd_salt = "SEU SALT"; //usado para criar as senhas do usuário no banco do GLPI
```

&nbsp;

## Possíveis erros

- Se aparecer o seguinte erro:
> ```php
> OAuthException: Unexpected result from the server "https://uspdigital.usp.br/wsusuario/oauth/request_token" () while requesting a request tokenobject(OAuthException2)
> ```
> 
> Use a variável `$regex_http_1dot1` na expressão if da linha 477 do arquivo `library/OAuthRequester.php`
