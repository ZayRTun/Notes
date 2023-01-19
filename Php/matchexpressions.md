**Home**
- [Home](../index.md)
---

# Match Expressions

```php
class Conversation {}

$obj = new Conversation();

// switch (get_class($obj)) {
// 	case 'Conversation':
// 		$type = 'started_conversation';
// 		break;

// 	case 'Reply':
// 		$type = 'replied_to_conversation';
// 		break;

// 	case 'Comment':
// 		$type = 'commented_to_lesson';
// 		break;
// }


// PHP 8 Match Expression

$type = match (get_class($obj)) {
	'Conversation' => 'started_conversation',
	'Reply' => 'replied_to_conversation',
	'Comment' => 'commented_on_lesson',
};

echo $type;
```