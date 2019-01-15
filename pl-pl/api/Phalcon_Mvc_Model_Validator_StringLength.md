* * *

layout: article language: 'en' version: '4.0' title: 'Phalcon\Mvc\Model\Validator\StringLength'

* * *

# Class **Phalcon\Mvc\Model\Validator\StringLength**

*extends* abstract class [Phalcon\Mvc\Model\Validator](/4.0/en/api/Phalcon_Mvc_Model_Validator)

*implements* [Phalcon\Mvc\Model\ValidatorInterface](/4.0/en/api/Phalcon_Mvc_Model_ValidatorInterface)

<a href="https://github.com/phalcon/cphalcon/tree/v4.0.0/phalcon/mvc/model/validator/stringlength.zep" class="btn btn-default btn-sm">Source on GitHub</a>

Simply validates specified string length constraints

This validator is only for use with Phalcon\Mvc\Collection. If you are using Phalcon\Mvc\Model, please use the validators provided by Phalcon\Validation.

```php
<?php

use Phalcon\Mvc\Model\Validator\StringLength as StringLengthValidator;

class Subscriptors extends \Phalcon\Mvc\Collection
{
    public function validation()
    {
        $this->validate(
            new StringLengthValidator(
                [
                    "field"          => "name_last",
                    "max"            => 50,
                    "min"            => 2,
                    "messageMaximum" => "We don't like really long names",
                    "messageMinimum" => "We want more than just their initials",
                ]
            )
        );

        if ($this->validationHasFailed() === true) {
            return false;
        }
    }
}

```

## Metody

public **validate** ([Phalcon\Mvc\EntityInterface](/4.0/en/api/Phalcon_Mvc_EntityInterface) $record)

Executes the validator

public **__construct** (*array* $options) inherited from [Phalcon\Mvc\Model\Validator](/4.0/en/api/Phalcon_Mvc_Model_Validator)

Phalcon\Mvc\Model\Validator constructor

protected **appendMessage** (*string* $message, [*string* | *array* $field], [*string* $type]) inherited from [Phalcon\Mvc\Model\Validator](/4.0/en/api/Phalcon_Mvc_Model_Validator)

Appends a message to the validator

public **getMessages** () inherited from [Phalcon\Mvc\Model\Validator](/4.0/en/api/Phalcon_Mvc_Model_Validator)

Returns messages generated by the validator

public *array* **getOptions** () inherited from [Phalcon\Mvc\Model\Validator](/4.0/en/api/Phalcon_Mvc_Model_Validator)

Returns all the options from the validator

public **getOption** (*mixed* $option, [*mixed* $defaultValue]) inherited from [Phalcon\Mvc\Model\Validator](/4.0/en/api/Phalcon_Mvc_Model_Validator)

Returns an option

public **isSetOption** (*mixed* $option) inherited from [Phalcon\Mvc\Model\Validator](/4.0/en/api/Phalcon_Mvc_Model_Validator)

Check whether an option has been defined in the validator options