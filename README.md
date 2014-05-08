SQLite-simple-store
===================

Super lightweight Zero configuration sqlite-based key => value store with expiration time for PHP.

Basically its a simple key value storage with and expireation field which will delete the value after it expires.
Also since its heavily influenced by redis, some of redis useful functions were implemented.

Stable Version 0.1


##Usage

```php
<?php 
//include the class
include_once('SQLite_simple_store.php');

//instanceate the class
$s = new SQLite_simple_store('user_table');

//simple set key => value
$s->set('name','oha');

//simple get value by key
echo $s->get('name'); //oha

//set with expiretion time
$s->set('token','asdjjrt788dsfjjj447586',6000);

//update value
$s->set('name','ohad');

//get all keys
var_dump($->keys());

//set a more complex value
$s->set('user_1',
    array(
        'user_id' =>  1,
        'email'   => 'email@mail.com',
        'meta'    =>  array(
            'user_meta1' => 'some value',
            'user_meta2' => 'some other value',
        )
    )
);

```

##Installation
###composer
To install and use via the composer PHP package manager just take these steps:

If you don’t already have one, create the file composer.json in the root of your new project that is going to use SQLite-simple-store.
Add the following to the composer.json file..
```
	{
	    "require": {
	        "agentejo/SQLite-simple-store": "dev-master"
	    }
	}
```
###git
```
	git clone https://github.com/bainternet/SQLite-simple-store.git
```

###manual
	    simply [download the latest version][1] and include it.

##Methods
####get($key,$default)
    gets a specific value based on key, if the value has expired false will be returned. you can pass a default value as a second parameter to be returned if no value exists or is expired.
####set($key,$value)
    stores a value in the database.
####del($key)
    Deletes a value of the given key.
####keys($validate)
    get all keys in the db.
    if $validate is true (default) expired keys and values will get deleted and will not be returned. set $validate to false to get all keys even if they have expired.
####exists($key)
    checks if a key exists and is not expired
####get_all($validate)
    get all values in the db.
    if $validate is true (default) expired values will get deleted and will not be returned. set $validate to false to get all values even if they have expired.
####delete_all()
    deletes all values from db.
####incr($key,$by = 1)
    increment value by $by (default = 1).
####decr($key,$by = 1)
    decrement value by (default = 1).
####count($key)
    returns the count of elements in a key assuming it is an array or object.
####rpush($key,$value)
    adds an element to a key (right).
####lpush($key,$value)
    adds an element to a key (left).
####lset($key,$idx,$value)
    sets the value of an element in a key by index.
####lindex($key,$idx)
    gets an element from a key by its index.


  [1]: https://github.com/bainternet/SQLite-simple-store/releases