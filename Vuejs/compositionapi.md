**Home**
- [Home](../index.md)
---

# Vue 3 Composition API

## Ref & Reactive
- Use **Ref** if you have a simple component with 1 or 2 pieces of state.
- Use **Reactive** if component has multiple pieces of state, Wrap **states** into an state object.
- Can also mix **Ref & Reactive**

## Using **Reactive**
```javascript
<script>
	import { reactive, computed, onMounted, onUnmounted, watch, ref } from "vue";

	export default {
		props: ["title"],

		// passing props
		setup(props) {
			// state
			const state = reactive({
				isItemsLeftVisible: false,
				isMouseVisible: false,
				todoFromInput: "",
				todoId: 4,
				todos: [
					{
						id: 1,
						description: "Finist Screencast",
						isComplete: false,
					},
					{
						id: 2,
						description: "Learn Vue 3",
						isComplete: false,
					},
					{
						id: 3,
						description: "Paint wall",
						isComplete: false,
					},
				],
			});


			// functions (methods)
			function addTodo() {
				state.todos.push({
					id: state.todoId,
					description: state.todoFromInput,
					isComplete: false,
				});

				state.todoId++;
				state.todoFromInput = "";
			}

			function deleteTodo(id) {
				state.todos = state.todos.filter((todo) => todo.id !== id);
			}


			// computed properties
			const itemsLeft = computed(() => state.todos.filter((todo) => !todo.isComplete).length);


			// lyfecycle hooks
			onMounted(() => {
				console.log("Todo mounted");
				console.log(props.title);
			});

			watch(
				() => state.todoId,
				(newValue, oldValue) => {
					console.log("New value: ", +newValue);
					console.log("Old value: ", +oldValue);
				}
			);


			// returning
			return {
				state,
				addTodo,
				deleteTodo,
				itemsLeft,
			};
		},
	};
</script>
```

## Using **Ref**
```javascript
<script>
	import { reactive, computed, onMounted, onUnmounted, watch, ref } from "vue";

	export default {
		props: ["title"],

		setup(props) {
			const isItemsLeftVisible = ref(false);
			const isMouseVisible = ref(false);
			const todoFromInput = ref("");
			const todoId = ref(4);
			const todos = ref([
				{
					id: 1,
					description: "Finist Screencast",
					isComplete: false,
				},
				{
					id: 2,
					description: "Learn Vue 3",
					isComplete: false,
				},
				{
					id: 3,
					description: "Paint wall",
					isComplete: false,
				},
			]);

			function addTodo() {
				todos.value.push({
					id: todoId.value,
					description: todoFromInput.value,
					isComplete: false,
				});

				todoId.value++;
				todoFromInput.value = "";
			}

			function deleteTodo(id) {
				todos.value = todos.value.filter((todo) => todo.id !== id);
			}

			const itemsLeft = computed(() => todos.value.filter((todo) => !todo.isComplete).length);

			onMounted(() => {
				console.log("Todo mounted");
				console.log(props.title);
			});

			watch(
				() => todoId.value,
				(newValue, oldValue) => {
					console.log("New value: ", +newValue);
					console.log("Old value: ", +oldValue);
				}
			);

			return {
				isItemsLeftVisible,
				isMouseVisible,
				todoFromInput,
				todoId,
				todos,
				addTodo,
				deleteTodo,
				itemsLeft,
			};
		},
	};
</script>

```