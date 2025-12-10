<script>
	import Button from './Button.svelte';

	let { name, logo, score, id } = $props();
</script>

<div class="card">
	<div class="info">
		<img src={logo} alt={`${name} logo`} />
		<p class="no-margin">{name}</p>
	</div>
	<div class="rating">
		<div class="score">{score?.toLocaleString(undefined, { style: 'percent' })}</div>
		<div class="buttons">
			{#if id !== undefined}
				<Button type="secondary" href={`./brand/${id}`}>Read why</Button>
			{/if}
		</div>
	</div>
</div>

<style>
	.card {
		box-sizing: border-box;

		display: flex;
		flex-direction: column;
		align-items: flex-start;
		padding: 0px;

		width: 300px;
		height: 300px;

		background: var(--light);
		border: 1px solid var(--level-1);
		border-radius: 10px;
		overflow: hidden;

		flex-shrink: 0;
	}

	.info {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		padding: 20px;
		gap: 20px;

		align-self: stretch;
	}

	.rating {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		padding: 20px;
		gap: 20px;

		background: var(--primary-green);

		align-self: stretch;
		flex-grow: 1;
	}

	img {
		width: 48px;
		height: 48px;
	}

	.score {
		font-style: normal;
		font-weight: 500;
		font-size: 24px;
		line-height: 29px;

		color: var(--level-2);

		flex-grow: 1;
	}
</style>
