**Home**
- [Home](../index.md)
---

# Inheritance

```php
class CoffeeMaker
{
    public function brew()
    {
        var_dump('Brewing the coffee');
    }
}
```

## Note the relation if not consider using Composition
- SpecialtyCoffeemaker is a Coffee maker

```php
class SpecialtyCoffeeMaker extends CoffeeMaker
{
    public function brewLatte()
    {
        var_dump('Brewing a latte');
    }
}

(new SpecialtyCoffeeMaker())->brewLatte();
```
-   It can brew a Coffee and also brew a Latte

## Another Example of Inheritance
```php
class Collection
{
    protected array $items;

    public function __construct(array $items)
    {
        $this->items = $items;
    }

    public function sum($key)
    {
        // It's better to use the Arrow fn to avoid using the `use` key word
        // return array_sum(array_map(fn($item) => $item->$key, $this->items));
        // Even better cause we are simply returning the array column
        return array_sum(array_column($this->items, $key));
    }
}

class VideosCollection extends Collection
{
    public function length()
    {
        return $this->sum('length');
    }
}

class Video
{
    public $title;
    public $length;

    public function __construct($title, $length)
    {
        $this->title = $title;
        $this->length = $length;
    }
}

$videos = new VideosCollection([
    new Video('Some Video', 100),
    new Video('Some Video 2', 200),
    new Video('Some Video 3', 300)
]);

echo $videos->length();
```

## Inheritance and `Override` parent behavior
- Tucking away the default to the base class

```php
class AchievementType
{
    public function name()
    {
        return $this->class_basename();
    }

    public function difficulty()
    {
        return 'intermediate';
    }

    public function icon()
    {
        return '/images/' . $this->class_basename() . '.png';
    }

    private function class_basename() {
        return strtolower( get_class($this) );
    }
}
```

### Looking at the class name we can figure out what the name and icon is and tuck away the defaults to the base class, here remained a clean class that is easy to modify in Special Cases we can Override the parent behavior
```php
class FirstThousandPoints extends AchievementType
{
    public function qualifier($user)
    {

    }

    public function name()
    {
        return 'New Name Overridden';
    }
}
var_dump((new FirstThousandPoints())->name());
```