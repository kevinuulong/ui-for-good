<!-- NOTE: Portions of this file are AI generated -->

<script>
	// 1. External State Management
	// $bindable() makes the `newReview` variable automatically update the

	import Button from './Button.svelte';

	// bound variable in the parent component when it is assigned a new value.
	let { reviews = $bindable(), open: isOpen = $bindable() } = $props();

	// 2. Internal Form State
	let form = $state({
		author: '',
		body: '',
		purchased: '',
		product: '',
		condition: 'Good' // Default value
	});

	// 3. Derived State for Form Validation
	const isFormValid = $derived.by(() => {
		// Simple validation: check if required fields are non-empty
		return (
			form.author.trim() !== '' &&
			form.body.trim() !== '' &&
			form.purchased.trim() !== '' &&
			form.product.trim() !== ''
		);
	});

	// 4. Action Handlers
	function handleSave() {
		if (!isFormValid) {
			alert('Please fill out all required fields.');
			return;
		}

		// Create the new review object
		const newReview = {
			author: form.author,
			body: form.body,
			purchased: form.purchased,
			product: form.product,
			condition: form.condition
		};

		// Update the bound array in the parent component.
		// Svelte handles the update propagation via the $bindable() rune.
		reviews = [newReview, ...reviews];

		// Reset the form and close the modal
		form = { author: '', body: '', purchased: '', product: '', condition: 'Good' };
		isOpen = false;
	}

	function handleClose() {
		isOpen = false;
		// Optionally reset form here if preferred, but only closing for now
	}

	function stopPropagation(e) {
		e.stopPropagation();
	}
</script>

{#if isOpen}
	<!-- svelte-ignore a11y_click_events_have_key_events -->
	<!-- svelte-ignore a11y_no_static_element_interactions -->
	<div class="modal-backdrop" onclick={handleClose}>
		<div class="modal-content" onclick={stopPropagation}>
			<h3 class="no-margin">New Review</h3>

			<form onsubmit={handleSave}>
				<div class="form-group">
					<label for="author">Author Name *</label>
					<input type="text" id="author" bind:value={form.author} required />
				</div>
				<div class="form-group">
					<label for="product">Product *</label>
					<input type="text" id="product" bind:value={form.product} required />
				</div>

				<div class="form-group">
					<label for="purchased">Purchased *</label>
					<input type="text" id="purchased" bind:value={form.purchased} required />
				</div>

				<div class="form-group">
					<label for="condition">Current Condition</label>
					<select id="condition" bind:value={form.condition}>
						<option value="Excellent">Excellent</option>
						<option value="Very Good">Very Good</option>
						<option value="Good">Good</option>
						<option value="Used">Used</option>
						<option value="Bad">Bad</option>
						<option value="Unusable">Unusable</option>
					</select>
				</div>

				<div class="form-group full-width">
					<label for="body">Review *</label>
					<textarea id="body" bind:value={form.body} required rows="4"></textarea>
				</div>

				<div class="form-actions">
					<button type="button" class="cancel" onclick={handleClose}>Cancel</button>
					<button type="submit" class="submit" disabled={!isFormValid}>Save</button>
				</div>
			</form>
		</div>
	</div>
{/if}

<style>
	button {
		box-sizing: border-box;

		display: flex;
		flex-direction: row;
		align-items: center;
		padding: 10px;
		gap: 10px;

		border: 1px solid var(--primary-green);
		border-radius: 5px;
		font-family: 'Instrument Sans', sans-serif;
		font-weight: 500;

		&.cancel {
			background-color: transparent;
			color: var(--primary-green);

			&:hover,
			&:focus {
				background-color: color-mix(in srgb, var(--dark) 10%, transparent);
			}
		}

        &.submit {
            background-color: var(--primary-green);
            color: var(--level-0);

            &:hover,
			&:focus {
				background-color: color-mix(in srgb, var(--dark) 10%, var(--primary-green));
			}

            &:disabled {
                background-color: color-mix(in srgb, transparent 50%, var(--primary-green));
                border-color: color-mix(in srgb, transparent 50%, var(--primary-green));
            }
        }
	}

	/* Basic Modal Styling for visibility */
	.modal-backdrop {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: rgba(0, 0, 0, 0.8);
		display: flex;
		justify-content: center;
		align-items: center;
		z-index: 1000;
	}

	.modal-content {
		background: white;
		padding: 2rem;
		border-radius: 8px;
		box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
		max-width: 500px;
		width: 90%;
	}

	/* Form Styling */
	form {
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: 20px;
	}

	.form-group label {
		display: block;
		margin-bottom: 5px;
		font-weight: 500;
	}

	.form-group input,
	.form-group select,
	.form-group textarea {
		width: 100%;
		padding: 8px;
		border: 1px solid var(--level-1);
		border-radius: 4px;
		box-sizing: border-box;
	}

	.full-width {
		grid-column: 1 / 3;
	}

	.form-actions {
		grid-column: 1 / 3;
		display: flex;
		justify-content: flex-end;
		gap: 10px;
		margin-top: 10px;
	}

	h3 {
		margin-bottom: 40px;
	}
</style>
