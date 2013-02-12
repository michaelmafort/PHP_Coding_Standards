PHP Padrões de Código
====================

Este documento descreve sobre padrões profissionais usados em projetos com o framework CakePHP.
Os padrões são baseados no PSR-1 e CakePHP Coding Standards.

Se você precisar utilizá-lo em seus projetos, sinta-se avontade.

1. Diretórios e Arquivos
-----------

- Para abrir tags php use somente `<?php`.

- Use somente UTF-8 sem BOM para seus códigos PHP, fazendo seu código mais limpo e padronizado, evitando problemas de codificação.

- Não use o mesmo arquivo para criar mais de uma classe.

- Nomes de classe devem ser declarados em `StudlyCaps`.

- Constantes de classes devem ser declarada com todas as letras em caixa alta, separando as palavras com underscore.

- Nomes de métodos devem ser declarados em `camelCase`.

- Não use o fechamento de tag php `?>` para classes e arquivos que serão incluídos.

- Nomes de diretórios devem ser escritos em `StudleCaps`.

- Documente as variáveis, métodos e classes.

- Exemplos:

```php
//caminho do arquivo: Controller/PagesController.php
<?php
/**
 * Esta classe é um exemplo de classe com os padrões de escrita de código em PHP.
 *
 * PHP 5
 *
 * Company Name: (http://www.companyname.com)
 * Copyright 2005-2012, Company Name (http://www.companyname.com)
 *
 * Licensed under The MIT License
 * Redistributions of files must retain the above copyright notice.
 *
 * @copyright     Copyright 2005-2012, Company Name (http://www.companyname.com)
 * @link          http://www.companyname.com My Company link description
 * @package       app.Controller
 * @license       MIT License (http://www.opensource.org/licenses/mit-license.php)
 */
class PagesController extends AppController{

    /**
    * @var String
    * Descrição da constante
    */
    const NOME_DA_CONSTANTE = 'valor';
    
    /**
    * @var String
    * Descrição da variável
    */
    private $__nomeDaVariavel = 'valor';
    
    /**
    * @var String
    * Descrição da variável
    */
    protected $_nomeDaVariavel = 'valor';
    
    /**
    * @var String
    * Descrição da variável
    */
    public $nomeDaVariavel = 'valor';
    
    /**
    * @var String
    * Description of the variable
    */
    public static $staticVar = 'valor';
    
    /**
    * index
    * Descrição do comportamento do método
    * @param $param1 String Descrição do atributo
    * @return void
    */
    public function index($param1 = null) {
        //some code here
        $this->__process();
    }
  
    /**
    * process
    * Descrição do comportamento do método
    * @return array Lista de Usuários
    */
    private function __process() {
        //seu código aqui
        return array();
    }

}
```

2. Melhores práticas para estruturas, condições e loops.
----------

- Utilize 4 espaços para identação, substitua em sua IDE a tab por 4 espaços.

```php
class ClassName {
    public function nomeDoMetodo() {
        //conteúdo do método
    }
}
````

- Não utilize estruturas ternárias com vários níveis, utilize apenas para condições simples.
- Estruturas de IF, ELSE utilize as chaves logo após um espaçamento entre os parenteses e as chaves, inclua o ELSE na mesma linha de fechamento da chave do IF e utilize um espaçamento entre as chaves.
- Para métodos, funções e classes use as chaves após um espaço entre a nome da classe, interface ou traits.

```php
//Ternário errado
$result = $var == 1 ? 'output' : $var == 2 ? 'continue' : 'none';

//Ternário Correto
$isMale = ($var ==  'male') ? true : false;

//No caso abaixo, prefira utilizar estrutura de IF, ELSE
$result = 'none';
if($var == 1) {
    $result = 'output';
} else if($var == 2) {
    $result = 'continue';
}
```

- Funções devem ser chamados sem espaçamento entre o nome da função e seus parentesis, os espaços são usados somente para separar os atributos.

```php
$result = foo(1, 2, 3);
```

- Nomes de variáveis devem ser escritas utilizando o `camelCase`, exceto para instancias de classes, onde você deve utilizar para a variável o mesmo nome da classe.

```php
$PagesController = new PagesController();
```

- Métodos aninhados devem ser chamado um método por linha, utilizando um espaçamento de 4 caracteres.

```php
$ComponentName->init()
    ->isPost()
    ->params(array('url' => 'http://www.michaelmafort.com.br'))
    ->execute();
```

- Para comentários em linha use //.
- Para comentários multi linhas use /**/

```php
//COmentário em linha
/*
Comentário multi linha
Descreva seu conteúdo, comportamento, etc
*/
```

3. Inclusão de arquivos
-----------

Se você está usando o framework `CakePHP` as inclusões devem ser feitas pela classe estatica App, conforme exemplo abaixo:

```php
//para importar qualquer arquivo
//docs http://book.cakephp.org/2.0/en/core-utility-libraries/app.html#including-files-with-app-import
App::import(mixed $type = null, string $name = null, mixed $parent = true, array $search = array(), string $file = null, boolean $return = false);

//Para importar objetos do framework
App::uses('PostsController', 'Controller');
App::uses('AuthComponent', 'Controller/Component');
App::uses('MyModel', 'Model');
App::uses('TreeBehavior', 'Model/Behavior');
App::uses('ThemeView', 'View');
App::uses('HtmlHelper', 'View/Helper');
App::uses('PaymentProcessor', 'Lib');
App::uses('Textile', 'Vendor');
App::uses('String', 'Utility');
```
