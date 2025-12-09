<script>
	let { children } = $props();
</script>

<button>
	{@render children()}
</button>

<style>
	button {
		font-family: 'Instrument Sans';
		font-style: normal;
		font-weight: 400;
		font-size: 16px;
		line-height: 20px;
		/* identical to box height */
		text-decoration-line: underline;

		color: var(--primary-green);

		background-color: transparent;
		border: none;

		display: flex;
		flex-direction: row;
		align-items: center;
		padding: 10px;
		gap: 10px;

		border-radius: 5px;

        &:hover, &:focus {
            background-color: var(--dark-10);
        }
	}
</style>
