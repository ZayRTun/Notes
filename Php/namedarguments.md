**Home**
- [Home](../index.md)
---

# Named arguments


```php
class Invoice
{
	private $description;
	private $total;
	private $date;
	private $paid;

	public function __construct($description, $total, $date, $paid)
	{
		$this->description = $description;
		$this->total = $total;
		$this->date = $date;
		$this->paid = $paid;
	}
}

// The old ways. here the order matters. 
// Hard to remember which is what
// $invoice = new Invoice(
// 	'customer installation',
// 	10000.00,
// 	new DateTime(),
// 	true
// );

// PHP 8, with named arg the order doesnt matter anymore
$invoice = new Invoice(
	date: new DateTime(),
	paid: true,
	description: 'customer installation',
	total: 10000.00,
);

var_dump($invoice);

```