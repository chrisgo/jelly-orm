# Jelly ORM

This is just a rewrite of the ORM found here https://github.com/creatoro/jelly
originally for the Kohana framework https://koseven.dev/

* Removed the Kohana-style HMVC (the loading of files on top of each other) which was innovative at the time
* Namespaced to Jelly and also copied the Kohana database classes (Database and DB)

## Usage

You will to create models (this will not magically infer fields from the database table.  
This allows you to do the lowerCamelCase field names (unlike Eloquent where you use snake_case)
and the fields are defined field-by-field (unlike Eloquent where it is by $fillable, $casts, etc.)

```php

class User extends \Jelly\Model {

  public static function initialize(\Jelly\Meta $meta) {
    $meta->fields([
      'name' => \Jelly::field('string', [
        'column' => 'name',
        'convert_empty' => true,
        'label' => 'name',
        'rules' => [[
          'maxlength' => 50,
         ]],
       ]),
       ...
    ]);
   }
}

// Then call it

$user = Jelly::factory('User', $id);
```




