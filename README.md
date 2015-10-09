
Origami ORM V 0.0.10 / Documentation


Origami ORM was build for CodeIgniter3 application, it's a programming technique for converting data between 
incompatible type systems in object-oriented programming languages.

WHY USE ORIGAMI ORM ?

  - Security 
      Origami can encoding file in base64 and encrypting adress (certified eTrust).
  
  - Lighter than others
      Origami only use essential package.

  - Friendly use :
      Easy and better understand.
      

  - Model Generator :
      Model Generator is a controller who create automatically your entity, you don't need to create them manually.
      
      
                                  --------------------------------------
                                  
                                  
                                  
                                  I - Model_exemple
                                  
  Construct : 
  few exemple of dependence in the construct function.
     
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
                                  
                                  
