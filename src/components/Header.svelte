<script>
	export let totalTodos;
	export let remainingTodos;
</script>

<!-- Header with information -->
<div class="app-header">
	<div>{totalTodos} Todos</div>
	<div class="task-count">{remainingTodos} Remaining</div>
</div>

<!-- Headers Styles -->
<style>
	.app-header {
		padding: 10px;
		display: flex;
		justify-content: space-between;
	}
	.task-count {
		align-self: center;
	}
</style>
