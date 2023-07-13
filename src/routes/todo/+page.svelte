<!-- importing components -->
<script>
	import Header from '../../components/Header.svelte';
	import Form from '../../components/Form.svelte';
	import Todos from '../../components/Todos.svelte';
	let todos = [
		{ id: 1, text: 'ehlo', completed: false },
		{ id: 2, text: 'lo', completed: true },
		{ id: 3, text: 'hlo', completed: false }
	];
	function onComplete(event) {
		let updateId = event.detail.id;
		todos.map((todo) => {
			if (todo.id === updateId) todo.completed = !todo.completed;
		});
		todos = todos;
	}
</script>

<!-- main container -->
<div id="app-container" class="app-container">
	<Header />
	<Todos {todos} on:completed={onComplete} />
	<Form />
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
