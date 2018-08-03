# What is PHP PNGQuant

PHP-PNGQuant is a non-official wrapper for the great [PNGQuant](https://github.com/pornel/pngquant), the command-line utility and a library for lossy compression of PNG images.

# Requirements

You need `pngquant` accesible from the PATH. If the utility isn't available for any reason, you can change the path to the binary using the `setBinaryPath` method:

```php
<?php

use ourcodeworld\PNGQuant\PNGQuant;

$instance = new PNGQuant();

// Change the path to the binary of pngquant, for example in windows would be (with an example path):
$instance->setBinaryPath("C:\\Users\\sdkca\\Desktop\\pngquant.exe")
    // Other options of PNGQuant here
    ->execute();
```

# Installation

php-pngquant can be used either with or without Composer.

## With Composer

The preferred way to use php-pngquant is with Composer. Execute the following command to install this package as a dependency in your project:

```batch
composer require ourcodeworld/php-pngquant
```

## Without Composer

If you don't use composer, you can still use the wrapper. Download the [PNGQuant.php](https://github.com/ourcodeworld/php-pngquant/blob/master/src/PNGQuant.php) class from the repository and then use `require_once` to import it in your code:

```php
<?php

require_once("PNGQuant.php");

$instance = new PNGQuant();

// Configuration here ...
```
# Example

Save the file directly into a directory with a file name.

```php
// Include the class
use ourcodeworld\PNGQuant\PNGQuant;

$instance = new PNGQuant();

// Set the path to the image to compress
$exit_code = $instance->setImage("/a-folder/image-original.png")
    // Set the output filepath
    ->setOutputImage("/a-folder/image-compressed.png")
    // Overwrite output file if exists, otherwise pngquant will generate output ...
    ->overwriteExistingFile()
    // As the quality in pngquant isn't fixed (it uses a range)
    // set the quality between 50 and 80
    ->setQuality(50,80)
    // Execute the command
    ->execute();

// if exit code is equal to 0 then everything went right !
if(!$exit_code){
    echo "Image succesfully compressed";
}else{
    echo "Something went wrong (status code $exit_code)  with description: ". $instance->getErrorTable()[(string) $exit_code];
}
```

If you need the raw data of the image (store the binary data of the compressed image), you can use the `getRawOutput` function:

```php
// Include the class
use ourcodeworld\PNGQuant\PNGQuant;

$instance = new PNGQuant();

// Set the path to the image to compress
$result = $instance->setImage("/a-folder/image-original.png")
    // Overwrite output file if exists, otherwise pngquant will generate output ...
    ->overwriteExistingFile()
    // As the quality in pngquant isn't fixed (it uses a range)
    // set the quality between 50 and 80
    ->setQuality(50,80)
    // Retrieve RAW data from pngquant
    ->getRawOutput();

$exit_code = $result["statusCode"];


// if exit code is equal to 0 then everything went right !
if($exit_code == 0){

    $rawImage = imagecreatefromstring($result["imageData"]);

    // Example Save the PNG Image from the raw data into a file or do whatever you want.
    // imagepng($rawImage , 'newfile.png');

    echo "Image succesfully compressed, do something with the raw Data";
}else{
    echo "Something went wrong (status code $exit_code)  with description: ". $instance->getErrorTable()[(string) $exit_code];
}
```

# Documentation

For further information and examples of the wrapper, please [visit the official documentation here](http://docs.ourcodeworld.com/projects/php-pngquant).

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
