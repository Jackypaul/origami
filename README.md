
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
 
###Model
 



* **Dependence** :
    a few exemple of library dependance for origami in construct function.

 ```
     function __construct()
    {
        parent::__construct();

        // Dépendance
        $this->load->library('origami', array(
            'entity_autoload' => TRUE,
            'entity_path' => APPPATH.'third_party/origami/models/Entity',
            'binary_enable' => TRUE,
            'encryption_enable' => TRUE,
            'encryption_key' => bin2hex('Origami')
        ));
    }
    
    ```
    
 * **Add** :
     Origami return the state (trans_status) during the "get" and cancel it if any error occurs.
     
     ```
     public function add()
    {
        \Origami\DB::get('test')->trans_start();

        $user = new \Entity\test\user();
        $user->firstname = 'John';
        $user->lastname = 'Do';
        $user->password = sha1('JohnDo');
        $user->birth = new DateTime('17-04-1984');
        $user->dateinsert = new DateTime();
        $user->dateupdate = new DateTime();
        $user->save();
        
        \Origami\DB::get('test')->trans_complete();
        
        return \Origami\DB::get('test')->trans_status();
    }
    ```
    
     
 
