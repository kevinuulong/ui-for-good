<script>
	import { page } from '$app/stores';
	import BrandCard from '$lib/BrandCard.svelte';

	import brands from '$lib/brands.json';
	import Button from '$lib/Button.svelte';

	import AddIcon from '$lib/icons/Add.svg?raw';
	import Review from '$lib/Review.svelte';

	const brand = brands[$page.params.brand];
</script>

<main>
	<div class="scorecard">
		<BrandCard name={brand.name} score={brand.score} logo={brand.logo} />
	</div>
	<div class="reviews">
		<div class="heading">
			<h2 class="no-margin">Reviews</h2>
			<Button icon={AddIcon} type="hero" />
		</div>
		{#each brand.reviews as review}
			<Review {...review} />
		{/each}
	</div>
</main>

<style>
	main {
		height: calc(100% - 90px);

		box-sizing: border-box;

		display: flex;
		flex-direction: row;
		align-items: flex-start;
		align-content: flex-start;
		padding: 20px 80px;
		gap: 10px 40px;
	}

	.reviews {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		padding: 0px;
		gap: 40px;

		flex-grow: 1;
	}

	.heading {
		display: flex;
		flex-direction: row;
		align-items: center;
		padding: 0px;
		gap: 10px;

		align-self: stretch;
		flex-grow: 0;
	}

	h2 {
		flex-grow: 1;
	}
</style>
