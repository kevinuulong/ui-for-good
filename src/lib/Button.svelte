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
		box-sizing: border-box;

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

		text-decoration: none;
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
		border: 1px solid var(--level-2);
		color: var(--level-2);
		background: var(--primary-green);

        font-weight: 500;
        font-size: 16px;
        line-height: 20px;
        height: auto;


		&:hover,
		&:focus {
			background-color: color-mix(in srgb, var(--dark) 10%, var(--primary-green));
		}
	}

	.tertiary {
		color: var(--primary-green);
		background: transparent;

		&:hover,
		&:focus {
			background-color: color-mix(in srgb, var(--dark) 10%, transparent);
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
