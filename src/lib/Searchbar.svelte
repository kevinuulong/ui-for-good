<script>
	import SearchIcon from '$lib/icons/Search.svg?raw';

	let { value = $bindable() } = $props();
</script>

<div class="container">
	{@html SearchIcon}
	<input type="text" placeholder="What are you looking for today?" bind:value />
</div>

<style>
	.container {
		box-sizing: border-box;

		display: flex;
		flex-direction: row;
		align-items: center;
		padding-left: 20px;
		gap: 10px;

		background: var(--light);
		border: 1px solid var(--level-1);
		border-radius: 5px;

		align-self: stretch;

		color: var(--dark-80);

		&:focus-within {
			outline: auto;
		}
	}

	input {
		/* What are you looking for today? */
		border: none;

		font-family: 'Instrument Sans';
		font-style: normal;
		font-weight: 400;
		font-size: 24px;
		line-height: 29px;

		/* Inside auto layout */
		flex: none;
		order: 1;
		flex-grow: 1;
		padding: 20px;

		&:focus {
			outline: none;
		}
	}
</style>
