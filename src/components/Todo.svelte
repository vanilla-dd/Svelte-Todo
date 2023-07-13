<script>
	import { createEventDispatcher } from 'svelte';
	export let itemText;
	export let completed;
	export let itemId;
	const dispatch = createEventDispatcher();
	function markCheck(id) {
		dispatch('completed', { id: id });
	}
</script>

<li class="todo-list list-item-view {completed ? 'completed' : ''}">
	<span>
		<button
			on:click={markCheck(itemId)}
			class="btn btn-done fa-solid {completed ? 'fa-square-check' : 'fa-square'}"
		/>
		<span>{itemText}</span>
	</span>
	<button class="btn btn-delete fa-solid fa-trash" />
</li>

<!-- styles for each todo -->
<style>
	.btn {
		color: inherit;
		cursor: pointer;
		font-size: 15px;
		padding: 10px 12px;
		border-radius: 2em;
		background: none;
		border: 0px solid;
		transition: 250ms ease-out;
	}

	.btn:hover {
		background: #1d2025;
	}

	.btn:focus {
		outline: none;
	}

	.btn-delete {
		color: #666;
		font-size: 0.7em;
	}
	.todo-list:first-of-type {
		border-top: 1px solid rgb(121, 121, 121);
		padding-top: 10px;
	}

	.list-item-view {
		padding-top: 5px;
		padding-bottom: 0px;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}

	.completed {
		color: #6a6f75;
		opacity: 0.5;
	}
</style>
