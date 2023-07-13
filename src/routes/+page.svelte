<main>
	<h1>helo</h1>
	<a class="toTodo" href="/todo">Check todo</a>
</main>

<style>
	main {
		display: flex;
		flex-direction: column;
		gap: 2rem;
	}
	.toTodo {
		font-size: 2rem;
		text-decoration: none;
		color: white;
		font-weight: 900;
		position: relative;
	}
	.toTodo::before {
		content: '';
		position: absolute;
		height: 3px;
		background-color: red;
		width: 0;
		top: 30px;
		transition: width 400ms ease-in-out;
	}
	.toTodo:hover::before {
		width: 100%;
		color: red;
	}
</style>
