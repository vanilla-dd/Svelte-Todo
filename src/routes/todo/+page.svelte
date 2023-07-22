<!-- importing components -->
<script>
	import Header from '../../components/Header.svelte';
	import Form from '../../components/Form.svelte';
	import Todos from '../../components/Todos.svelte';
	import { onMount, afterUpdate } from 'svelte';
	import { browser } from '$app/environment';
	const TodosLocal = browser && JSON.parse(localStorage.getItem('todos'));
	let newText;
	let todos = [];
	let totalTodos;
	let remainingTodos;
	onMount(() => {
		loadTodos();
	});

	afterUpdate(() => {
		saveTodos();
	});
	function loadTodos() {
		const TodosLocal = browser && JSON.parse(localStorage.getItem('todos'));
		if (TodosLocal) {
			todos = TodosLocal;
		}
	}

	function saveTodos() {
		browser && localStorage.setItem('todos', JSON.stringify(todos));
	}
	$: totalTodos = todos.length;
	$: remainingTodos = todos.reduce((n, todo) => {
		return n + (todo.completed ? 0 : 1);
	}, 0);
	function onComplete(event) {
		let updateId = event.detail.id;
		todos.map((todo) => {
			if (todo.id === updateId) todo.completed = !todo.completed;
		});
		todos = todos;
	}
	function createTodo() {
		newText = newText.trim();
		if (newText !== '') {
			const newId = todos.length ? Math.max(...todos.map((e) => e.id)) + 1 : 1;
			todos = [...todos, { id: newId, text: newText, completed: false }];
		}
		newText = '';
	}
	function deleteTodo(event) {
		let delId = event.detail.id;
		todos = todos.filter((todo) => {
			return todo.id != delId;
		});
	}
</script>

<!-- main container -->
<div id="app-container" class="app-container">
	<Header {totalTodos} {remainingTodos} />
	<Todos {todos} on:completed={onComplete} on:delete={deleteTodo} />
	<Form bind:newText on:create={createTodo} />
</div>

<!-- styles for main container -->
<style>
	.app-container {
		width: 400px;
		min-height: 500px;
		background-color: #282c34;
		box-shadow: 0 20px 80px rgba(0, 0, 0, 0.6);
		background: radial-gradient(circle, #282c34 0%, rgba(40, 48, 56, 1) 100%);
		position: relative;
		border-radius: 1em;
		padding: 20px;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}
</style>
