PHP Coding Standards
====================

This document describe about a professional standards on my own project using CakePHP. 
The standards is base on PSR-1 e CakePHP Coding Standards.

If you need to use, feel free.

1. Directories and Files
-----------

- To open php script tags, use `<?php` or `<?=` if you like to print the output.

- Use only UTF-8 without BOM for PHP code, this make your code clean of charsets problems.

- Do not use the same file with more than one `Class`.

- Class names must be declared in `StudlyCaps`.

- Class constants must be declared in all upper case with underscore separators.

- Method names must be declared in `camelCase`.

- For Class file not close the php tag `?>`.

- Directory names must be named in `StudleCaps`.

- Document the variable, methods and classes.

- Samples:

```php
//filepath: Controller/PagesController.php
<?php
/**
 * This class is a sample class standards about the writing code in php.
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
    * Description of the constant
    */
    const VARIABLE_NAME = 'value';
    
    /**
    * @var String
    * Description of the variable
    */
    private $__variableName = 'value';
    
    /**
    * @var String
    * Description of the variable
    */
    protected $_variableName = 'value';
    
    /**
    * @var String
    * Description of the variable
    */
    public $variableName = 'value';
    
    /**
    * @var String
    * Description of the variable
    */
    public static $staticVar = 'value';
    
    /**
    * Function name
    * Description of the method behavior
    * @param $param1 String Description of the param1
    * @return void
    */
    public function index($param1 = null) {
        //some code here
        $this->__process();
    }
  
    /**
    * Function name
    * Description of the method behavior
    * @return array List of users
    */
    private function __process() {
        //some code here
        return array();
    }

}
```

2. Best practices for structures. Conditions and loops.
----------

- Use 4 (four) spaces to ident, replace on your IDE the tab for four spaces.

```php
class ClassName {
    public function nameMethod() {
        //method content
    }
}
````

- Do not use the nested ternary structure.
- Use ternary only for simple conditions.
- The if, else structure must be writed using the bracket after the closing parenthesis and one space between the parenthesis and bracket.
- For else if use on same line of the closing bracked of the if separeted by one space between the ending bracked and the else instruction.
- For methods, functions and classes use the bracked after one space of the class name, or extended class, interface or traits.

```php
//Never use the structure below.
$result = $var == 1 ? 'output' : $var == 2 ? 'continue' : 'none';

//In the case above prefer to use if, else structure
$result = 'none';
if($var == 1) {
    $result = 'output';
} else if($var == 2) {
    $result = 'continue';
}
```

- Function must be called without spaces between the function name and the parenthesis, the spaces is only used for separete function attributes.

```php
$result = foo(1, 2, 3);
```

- Variables names follow the write on camelCase, except for classes instances, where you use the same name of the Class.

```php
$PagesController = new PagesController();
```

- Nested methods use on method by line and ident the nexts methods by one tab (4 spaces)

```php
$ComponentName->init()
    ->isPost()
    ->params(array('url' => 'http://www.michaelmafort.com.br'))
    ->execute();
```

- Comments inline use //.
- Comments multiline use /**/

```php
//Coment inline
/*
Multiline comment
Describe your contents, todos, mistakes and jokes 
(I'm joking, of your write the jokes on your code, never write this :P)
*/
```

3. Includes
-----------

If you are using `CakePHP` framework the includes are maked by the App static class, something like this:

```php
//to import any file
//docs http://book.cakephp.org/2.0/en/core-utility-libraries/app.html#including-files-with-app-import
App::import(mixed $type = null, string $name = null, mixed $parent = true, array $search = array(), string $file = null, boolean $return = false);

//to import cakephp objects
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
