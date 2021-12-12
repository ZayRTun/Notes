**Home**
- [Home](../index.md)
---

# Incapsulation

## Encapsulation => Enclose withing a capsule
### **private** & **protected**
- `private` means this class can alone access the method
- `protected` means this and all it's **sub classes** class can access this method

```php
<?php
class TennisMatch
{
    public function score()
    {
        // is there a winner
        // does someone have an advantage
        // are that in deuce
    }

    protected function hasWinner()
    {

    }

    protected function hasAdvantage()
    {

    }

    protected function inDeuce()
    {

    }
}
