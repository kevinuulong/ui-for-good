<script>
	import Button from '$lib/Button.svelte';
	import ArrowRightAltIcon from '$lib/icons/ArrowRightAlt.svg?raw';
	import Polaroid from '$lib/assets/redwood_polaroid.jpg';
	import Searchbar from '$lib/Searchbar.svelte';
	import BrandCard from '$lib/BrandCard.svelte';

	import brands from '$lib/brands.json';

	import Fuse from 'fuse.js';

	let searchTerm = $state('');

	const fuse = new Fuse(brands, {
		keys: ['name', 'description', 'keywords'],
		findAllMatches: true,
		ignoreDiacritics: true,
		shouldSort: false,
		threshold: 0.25
	});

	const filtered = $derived.by(() => {
		if (searchTerm.trim() === '') {
			return brands;
		}
		const results = fuse.search(searchTerm);
		return results.map((result) => result.item);
	});

	const recommended = $derived.by(() => {
		return filtered.filter((brand) => brand.score >= 0.8);
	});

	const avoid = $derived.by(() => {
		return filtered.filter((brand) => brand.score < 0.8);
	});
</script>

<main>
	<div class="hero">
		<h1 class="no-margin">Find the last _____ you’ll ever need</h1>
		<div class="text">
			<p class="no-margin">Tired of buying cheap junk that never lasts?</p>
			<p class="no-margin">
				Us too! That’s why we’ve found the products and brands that will last you a lifetime!
			</p>
		</div>
		<Button type="hero" icon={ArrowRightAltIcon} href="#brands">Browse brands</Button>
		<img src={Polaroid} alt="A Polaroid of a redwood forest" />
	</div>
	<div class="search-container">
		<Searchbar bind:value={searchTerm} />
	</div>
	<div class="brands-container" id="brands">
		<div class="heading">
			<h2 class="no-margin" id="recommend">Brands we recommend</h2>
			<p class="no-margin">
				Our community has tried and vetted these brands. We’re confident they make products that are
				designed to last!
			</p>
		</div>
		<div class="carousel">
			{#each recommended as brand}
				<BrandCard {...brand} />
			{/each}
		</div>
		<div class="heading">
			<h2 class="no-margin" id="avoid">Brands to avoid</h2>
			<p class="no-margin">
				Steer clear of these brands! These companies make products destined for the dumps.
			</p>
		</div>
		<div class="carousel">
			{#each avoid as brand}
				<BrandCard {...brand} />
			{/each}
		</div>
	</div>
    <div class="spacer"></div>
</main>

<style>
	main {
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 20px 80px;
		gap: 20px;

		height: calc(100% - 90px);

		box-sizing: border-box;
	}

    .spacer {
        height: 40px;
    }

	.hero {
		box-sizing: border-box;

		display: flex;
		flex-direction: column;
		align-items: flex-start;
		padding: 80px 60px;
		gap: 40px;
		isolation: isolate;

		height: 700px;

		background: var(--primary-green);
		border: 1px solid var(--level-1);
		border-radius: 10px;

		flex: none;
		order: 0;
		align-self: stretch;
		flex-grow: 0;

		position: relative;
	}

	h1 {
		color: var(--level-2);
		max-width: 500px;
	}

	.text {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		padding: 0px;
		gap: 20px;

		max-width: 500px;

		color: var(--secondary-green);
		margin-bottom: auto;
	}

	img {
		position: absolute;
		width: 23vw;
		max-width: 443.7px;
		right: -0.75vw;
		top: 64px;

		z-index: -9;

		box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.5);
		border-radius: 2px;
		transform: rotate(6.53deg);
	}

	.search-container {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		padding: 20px 0px;
		gap: 40px;

		align-self: stretch;
	}

	.brands-container {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		padding: 0px;
		gap: 40px;
		align-self: stretch;
	}

	.carousel {
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		align-items: flex-start;
		align-content: flex-start;
		padding: 0px;
		gap: 40px;

		align-self: stretch;
	}
</style>
