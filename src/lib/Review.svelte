<script>
	let { author, body, purchased, product, condition } = $props();
</script>

<div class="container">
	<div class="body">
		<div class="author">{author}</div>
		<p class="no-margin">
			{body}
		</p>
	</div>
	<div class="table">
		<div class="row">
			<div class="label">Purchased:</div>
			<div class="value">{purchased}</div>
		</div>
		<div class="row">
			<div class="label">Product:</div>
			<div class="value">{product}</div>
		</div>
		<div class="row">
			<div class="label">Current Condition:</div>
			<div class="value">{condition}</div>
		</div>
	</div>
</div>

<style>
	.container {
		display: flex;
		flex-direction: row;
		align-items: flex-start;
		padding: 20px;
		gap: 20px;

		background: var(--light);
		border-radius: 10px;

		align-self: stretch;
	}

	.body {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		padding: 0px;
		gap: 10px;

		flex-grow: 1;
		align-self: stretch;
	}

	.author {
		font-family: 'Instrument Sans';
		font-style: normal;
		font-weight: 500;
		font-size: 24px;
		line-height: 29px;
	}

	p {
		font-family: 'Instrument Sans';
		font-style: normal;
		font-weight: 400;
		font-size: 16px;
		line-height: 20px;

		align-self: stretch;
	}

	.table {
		box-sizing: border-box;

		display: flex;
		flex-direction: column;
		align-items: flex-start;
		padding: 0px;

		width: 350px;

		border: 1px solid var(--level-1);
		border-radius: 5px;

		flex-grow: 0;
		flex-shrink: 0;
	}

	.row {
		display: flex;
		flex-direction: row;
		align-items: center;
		padding: 10px;
		gap: 20px;

		align-self: stretch;
		flex-grow: 0;
	}

	.row:nth-of-type(even) {
		background-color: var(--level-0);
	}

	.label {
		font-weight: 500;
	}

	.value {
		text-align: right;
		flex: none;
		flex-grow: 1;
	}
</style>
