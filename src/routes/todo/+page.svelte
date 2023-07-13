<!-- importing components -->
<script>
	import Header from '../../components/Header.svelte';
	import Form from '../../components/Form.svelte';
	import Todos from '../../components/Todos.svelte';
</script>

<!-- main container -->
<div id="app-container" class="app-container">
	<Header />
	<Todos />
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
