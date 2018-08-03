# What is Name That Color

This library is a PHP port of the known JS Script to find out the closest color name by its hex code.
 
# Installation

Name That Color can be used either with or without Composer.

## With Composer

The preferred way to use name-that-color is with Composer. Execute the following command to install this package as a dependency in your project:

```batch
composer require ourcodeworld/name-that-color
```

## Without Composer

If you don't use composer, you can still use the wrapper. Download the [ColorInterpreter.php](https://github.com/ourcodeworld/name-that-color/blob/master/src/ColorInterpreter.php) class from the repository and then use `require_once` to import it in your code:

```php
<?php

require_once("ColorInterpreter.php");

$instance = new ColorInterpreter();

// Configuration here ...
```
# Example

Include the ColorInterpreter class and call the name method that returns an array with the closest color interpretation providen by the script. The result array contains three keys:

- hex: the hex color of the closest color in the class.
- name: the human name given to the color.
- exact: boolean that determines wheter the color code is exact as the name or not.

```php
// Include the class
use ourcodeworld\NameThatColor\ColorInterpreter as NameThatColor;

$instance = new NameThatColor();

$result = $instance->name("#008559");

var_dump($result);

array(3) {
  ["hex"]=>
  string(7) "#01826B"
  ["name"]=>
  string(8) "Deep Sea"
  ["exact"]=>
  bool(false)
}
```

This class offers other utilities as converting an hex color code to HSL or RGB as well in case you need them:

```php
// Include the class
use ourcodeworld\NameThatColor\ColorInterpreter as NameThatColor;

$instance = new NameThatColor();

// From hex to HSL
$hsl_data = $instance->hsl("#008559");
var_dump($hsl_data);
array(3) {
  [0]=>
  int(113)
  [1]=>
  int(255)
  [2]=>
  int(66)
}

// From hex to RGB
$rgb_data = $instance->rgb("#008559");
var_dump($rgb_data);
array(3) {
  [0]=>
  int(0)
  [1]=>
  int(133)
  [2]=>
  int(89)
}

```


The MIT License (MIT)
=====================

Copyright © 2017 Our Code World

Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the “Software”), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.
