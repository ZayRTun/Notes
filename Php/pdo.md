**Home**
- [Home](../index.md)
---

# PDO
## Always wrap PDO connections in a try and catch block
```php
try {
    $pdo = new PDO('mysql:host=127.0.0.1;dbname=mytodo', 'root', 'devpassword');
} catch (PDOException $e) {
    die($e->getMessage());
}
```

## PDO prepare the following statement
```php
$statement = $pdo->prepare('select * from todos');

$statement->execute();
```

- Fetch everything into memory and storing each column/row into an OBJECT -> PDO::FETCH_OBJ
- Here we are fetching everything into an DUMMY OBJECT
```php
$tasks = $statement->fetchAll(PDO::FETCH_OBJ);
```

## We can also fetch into a Class of our own, using the PDO::FETCH_CLASS
```php
$tasks = $statement->fetchAll(PDO::FETCH_CLASS, 'Task');
```
