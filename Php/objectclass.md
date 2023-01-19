**Home**
- [Home](../index.md)
---

# Object class `$obj::class`

```php
class Conversation {}

$obj = new Conversation();

// switch ($obj::class) {
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

$type = match ($obj::class) {
	'Conversation' => 'started_conversation',
	'Reply' => 'replied_to_conversation',
	'Comment' => 'commented_on_lesson',
};
```