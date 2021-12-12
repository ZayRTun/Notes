**Home**
- [Home](../index.md)
---

# Extraction

## Extraction for reusibility

### **useMousePosition.js**
```javascript
import { onMounted, onUnmounted, reactive, toRefs } from 'vue';

export function useMousePosition() {
	const pos = reactive({
		x: 0,
		y: 0,
	})

	function update(e) {
		pos.x = e.pageX;
		pos.y = e.pageY;
	}

	onMounted(() => {
		window.addEventListener("mousemove", update);
	});

	onUnmounted(() => {
		window.removeEventListener("mousemove", update);
	});

	return toRefs(pos)
}
```

**Usage in Component**
```html
<template>
	<div>x: {{ pos.x }}</div>
	<div>y: {{ pos.y }}</div>
</template>
```

```javascript
// import extracted function
<script>
import { useMousePosition } from "../functions/useMousePosition";

export default {
	props: ["title"],

	setup(props) {

		const pos = useMousePosition();

		return {
			pos,
		}
	}
}
</script>
```

## Another Example
### **useToggle.js**
```javascript
import { ref } from 'vue'

export function useToggle() {
	const isVisible = ref(false)

	function toggleVisible() {
		isVisible.value = !isVisible.value
	}

	return {
		isVisible,
		toggleVisible
	}
}

```

## **Usage in Component**

```html
<template>
	<div class="space-x-4">
		<button class="px-2 py-2 rounded bg-blue-500 text-white" @click="toggleItemsLeft">
			Toggle Items Left
		</button>
		<button class="px-2 py-2 rounded bg-blue-500 text-white" @click="toggleMouseVisible">
			Toggle Mouse Position
		</button>
	</div>

	<div>
		<div v-show="isItemsLeftVisible" class="border-t border-gray-500 py-2 mt-6">
			Items Left: {{ itemsLeft }}
		</div>
		<div v-show="isMouseVisible" class="border-t border-gray-500 py-2 mt-1">
			<div>x: {{ pos.x }}</div>
			<div>y: {{ pos.y }}</div>
		</div>
	</div>
</template>
```


```javascript
<script>
// import extracted function
import { useToggle } from "../functions/useToggle";

export default {
	props: ["title"],

	setup(props) {

		const { isVisible: isItemsLeftVisible, toggleVisible: toggleItemsLeft } = useToggle();
		const { isVisible: isMouseVisible, toggleVisible: toggleMouseVisible } = useToggle();

		return {
			isMouseVisible,
			toggleMouseVisible,
			isItemsLeftVisible,
			toggleItemsLeft,
		}
	}
}
</script>
```