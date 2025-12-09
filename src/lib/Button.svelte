<script>
	let { children, type = 'primary', icon, ...rest } = $props();

	const isIconButton = icon && !children;
</script>

{#if rest.href !== undefined}
	<a class={[type, { icon, 'icon-button': isIconButton }]} {...rest}>
		{@render children?.()}
		{#if icon}
			{@html icon}
		{/if}
	</a>
{:else}
	<button class={[type, { icon, 'icon-button': isIconButton }]} {...rest}>
		{@render children?.()}
		{#if icon}
			{@html icon}
		{/if}
	</button>
{/if}

<style>
	button,
	a {
		/* Frame 6 */

		box-sizing: border-box;

		/* Auto layout */
		display: flex;
		flex-direction: row;
		align-items: center;
		padding: 10px;
		gap: 10px;

		height: 49px;

		border-radius: 5px;

		font-family: 'Instrument Sans';
		font-style: normal;
		font-weight: 500;
		font-size: 24px;
		line-height: 29px;

		border: none;
	}

	.icon-button {
		width: 36px;
		height: 36px;
		padding: 0;

		justify-content: center;
	}

	.hero {
		border: 1px solid var(--secondary-green);
		background-color: var(--primary-green);
		color: var(--secondary-green);

		&:hover,
		&:focus {
			background-color: color-mix(in srgb, var(--dark) 10%, var(--primary-green));
		}
	}

	.primary {
		color: var(--Primary-White, #fff);
		background: var(--Primary-UC-Red, #e00122);

		&:hover,
		&:focus {
			background-color: color-mix(in srgb, var(--Primary-UC-Black) 10%, var(--Primary-UC-Red));
		}
	}

	.secondary {
		color: var(--Primary-UC-Black);
		background: var(--Secondary-Grey, #f3f3f3);

		&:hover,
		&:focus {
			background-color: color-mix(in srgb, var(--Primary-UC-Black) 10%, var(--Secondary-Grey));
		}
	}

	.tertiary {
		color: var(--primary-green);
		background: transparent;

		&:hover,
		&:focus {
			background-color: var(--dark-10);
		}
	}

	.link {
		color: var(--Primary-UC-Red);
		background: transparent;
		text-decoration: underline;

		&:hover,
		&:focus {
			background-color: color-mix(in srgb, var(--Primary-UC-Black) 10%, transparent);
		}
	}
</style>
