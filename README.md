
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
 



- **Dependence** :
*a few exemple of library dependance for origami in construct function.*

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
- **Add** :
*Origami return the state (trans_status) during the "get" and cancel it if any error occurs.*
     
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
- **Add_user_address** : 
 *the find_one() is use to get one user_id.*
   
```
   public function add_user_address()
    {
        $user = \Entity\test\user::find_one();

        $address = new \Entity\test\address();
        $address->user_id = $user->id;
        $address->street = '1 Promenade des Anglais';
        
        return $address->save();
    }
```

- **Add_user_file** :
  *In this exemple, the png file is encoding in base64.*

```
     public function add_user_file()
    {
        $user = \Entity\test\user::find_one();

        $file = new \Entity\test\file();
        $file->user_id = $user->id;
        $file->type = 'png';
        $file->content = base64_encode(file_get_contents('https://www.google.fr/images/srpr/logo11w.png'));

        return $file->save();
    }
```
 
- **Get** :
 *the get function use find_one() and return the variable in a array.*

```
  public function get()
    {
        $user = \Entity\test\user::find_one();
        $user = new \Entity\test\user($user->id);
        
        return $user->toArray();
    }
```
 
- **get_join** :
 *You can join some entity.*

```
   public function get_join()
    {
        $user = \Entity\test\user::find_one();

        $result = $user
            ->join(\Entity\test\file::entity())
            ->join(\Entity\test\address::entity())
            ->find_one();

        return $result->toArray();
    }
```
 - **get_user_adress** :
 
   ```
    public function get_user_address()
    {
        $user = \Entity\test\user::find_one();
        
        $address = $user->address()->find_one();

        return $address->toArray();
    }
    ```
 - **get_user_file** :
 
   ```
    public function get_user_file()
    {
        $file = \Entity\test\file::find_one();
        
        return $file->toArray();
    }
 ```
- **set** :
*In this exemple the set function find the firstname of the user table in the Entity and save it.*
```
    public function set()
    {
        $user = \Entity\test\user::find_one();
        $user->firstname = 'John';

        return $user->save();
    }
 ```
 - **Del** :
*The function del remove the table.*
  
```
    public function del()
    {
        $user = \Entity\test\user::find_one();

        return $user->remove();
    }
```
----------------
##Controller

- **index** :
*A exemple of a basic controller with function index using origami model*

```
 class Origami_test extends CI_Controller
{

    public function __construct()
    {
        parent::__construct();
        
        // Dépendances
        $this->load->library('unit_test');
        
        $this->load->add_package_path(APPPATH.'third_party/origami');
        $this->load->model('test_model');
        $this->load->remove_package_path(APPPATH.'third_party/origami');
        
        // Activation du profiler
        $this->output->enable_profiler();
    }

    public function index()
    {
        $this->unit->run($this->test_model->add(), TRUE, "Insert + Transaction");
        $this->unit->run($this->test_model->add_user_address(), TRUE, "Insert + cryptage");
        $this->unit->run($this->test_model->add_user_file(), TRUE, "Insert + binaire");
        $this->unit->run($this->test_model->get(), 'is_array', "Select");        
        $this->unit->run($this->test_model->get_join(), 'is_array', "Select + Join");
        $this->unit->run($this->test_model->get_user_address(), 'is_array', "Select + relation + cryptage");
        $this->unit->run($this->test_model->get_user_file(), 'is_array', "Select + binaire");
        $this->unit->run($this->test_model->del(), TRUE, "Delete");
        $this->output->set_output($this->unit->report());
    }

}
```


--------------
## Entity

- **Adresse** :
*A exemple of adresse Entity generate by Origami_generator.*

```
class address extends \Origami\Entity {
    
	public static $table = 'address';
    
	/**
	 * @property integer $id
	 * @property integer $user_id
	 * @property string $street
	 */
	public static $fields = array(
		array('name' => 'id', 'type' => 'int'),
		array('name' => 'user_id', 'type' => 'int'),
		array('name' => 'street', 'type' => 'string', 'allow_null' => true, 'encrypt' => TRUE),
		array('name' => 'vector', 'type' => 'string', 'allow_null' => true)
	);
    
	public static $primary_key = 'id';
    
	public static $associations = array(
		array('association_key' => 'user', 'entity' => '\Entity\test\user', 'type' => 'belongs_to', 'primary_key' => 'id', 'foreign_key' => 'user_id')
	);
}
```
--------------

 
