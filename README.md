
#Origami ORM V 0.0.10 / Documentation


Origami ORM was build for CodeIgniter3 application, it's a programming technique for converting data between 
incompatible type systems in object-oriented programming languages.

#####**WHY USE ORIGAMI ORM ?**

  * **Security** : 
      Origami can encoding file in base64 and encrypting adress (certified eTrust).
  
  * **Lighter than others** :
      Origami only use essential package.

  * **Friendly use** :
      Easy and better understand.
      

  * **Model Generator** :
      Model Generator is a controller who create automatically your entity, you don't need to create them manually
                                  
----------
# Schema
- Validation


```
<?php

namespace Origami\Entity\Shema;

defined('BASEPATH') OR exit('No direct script access allowed');

/**
 * Origami ORM (objet relationnel mapping)
 * @author Yoann VANITOU
 * @license http://www.apache.org/licenses/LICENSE-2.0
 * @link https://github.com/maltyxx/origami
 */
class Validation
{
    const OPTION_TYPE_EMAIL = 'email';
    const OPTION_TYPE_URL = 'url';
    const OPTION_TYPE_IP = 'ip';
    const OPTION_TYPE_INT = 'int';
    const OPTION_TYPE_FLOAT = 'float';
    const OPTION_TYPE_EXCLUSION = 'exclusion';
    const OPTION_TYPE_INCLUSION = 'inclusion';
    const OPTION_TYPE_FORMAT = 'format';
    const OPTION_TYPE_LENGTH = 'length';
    const OPTION_TYPE_PRESENCE = 'presence';
    const OPTION_TYPE_CALLBACK = 'callback';
    const OPTION_MIN = 'min';
    const OPTION_MAX = 'max';
    const OPTION_LIST = 'list';
    const OPTION_MATCHER = 'matcher';
    const OPTION_CALLBACK = 'callback';
    const OPTION_MESSAGE = 'message';
}

- Association
- Field
- Table
- Primary key
	
# CRUD
- Create
- edit
- delete

# RelationShip

# Query Builder

# Transaction

# Secuity
- Encryption
- Encoding

| Var | Name |
| ------------- | ----------- |
| OPTION_TYPE_EMAIL      | email |
| OPTION_TYPE_URL     | url     |
| OPTION_TYPE_IP     | ip     |
| OPTION_TYPE_INT     | int     |
| OPTION_TYPE_FLOAT     | float     |
| OPTION_TYPE_EXCLUSION     | exclusion     |
| OPTION_TYPE_INCLUSION     | inclusion     |
| OPTION_TYPE_FORMAT     | format     |
| OPTION_TYPE_LENGHT     | lenght     |
| OPTION_TYPE_PRESENCE     | presence     |
| OPTION_TYPE_CALLBACK     | callback     |
| OPTION_MIN     | min     |
| OPTION_MAX     | max     |
| OPTION_LIST     | list     |
| OPTION_MATCHER     | matcher     |
| OPTION_CALLBACK     | callback     |
| OPTION_MESSAGE     | message     |


----------
	

 
