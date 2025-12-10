<script>
	import Logo from '$lib/assets/logo.svg?raw';
	import NavbarItem from './NavbarItem.svelte';

	import AccountCircleIcon from '$lib/icons/AccountCircle.svg?raw';
	import Button from './Button.svelte';
</script>

<nav>
	<div class="links">
		<NavbarItem>Brands</NavbarItem>
		<NavbarItem>Categories</NavbarItem>
	</div>
	<a href="./" class="logo">
		{@html Logo}
	</a>
	<div class="icons">
		<Button icon={AccountCircleIcon} type="tertiary" />
	</div>
</nav>

<style>
	nav {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		padding: 10px 80px;
		gap: 10px;
		isolation: isolate;

		height: 90px;

		color: var(--primary-green);

		position: relative;

		box-sizing: border-box;
	}

	.logo {
		color: var(--primary-green);

		position: absolute;
		left: 50%;
		transform: translateX(-50%);
	}

	.links {
		display: flex;
		flex-direction: row;
		align-items: center;
		padding: 0px;
		gap: 20px;

		flex: none;
		order: 0;
		flex-grow: 0;
		z-index: 0;
	}

	.icons {
		display: flex;
		flex-direction: row;
		align-items: center;
		padding: 0px;
		gap: 20px;
	}
</style>
