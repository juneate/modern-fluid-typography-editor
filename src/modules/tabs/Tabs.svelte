<script>
	export let tabs;

	let activeTab = 0;
</script>

<article class="tabs-wrapper">
	<slot name="util" />
	<nav class="tabs">
		{#each tabs as label, index}
			<button
				class:tab__button--active={index === activeTab}
				class="tab__button"
				on:click={() => {
					activeTab = index;
				}}>{label}</button
			>
		{/each}
	</nav>
</article>

<slot {activeTab} />

<style>
	.tabs-wrapper {
		align-items: flex-end;
		justify-content: space-between;
		margin-bottom: var(--spacing-1);
		isolation: isolate;

		@media (--mq-desktop-min) {
			display: flex;
		}
	}

	.tabs {
		display: flex;
		margin-top: var(--spacing-1);

		@media (--mq-desktop-min) {
			margin-top: 0;
		}
	}

	.tab__button {
		background: transparent;
		border-width: 0;
		padding: var(--spacing-n1) var(--spacing-1);
		color: var(--color-gray-light);
		font-family: var(--font-family-primary);
		cursor: pointer;
		background-color: var(--color-gray-medium-faded);
		text-align: center;
		display: block;
		border: 2px solid currentColor;
		border-radius: var(--spacing-n1) 0 0 var(--spacing-n1);
		flex-grow: 1;

		@media (--mq-mobileLandscape-min) {
			flex-grow: initial;
			min-width: calc(2 * var(--spacing-4));
			padding: var(--spacing-n1) var(--spacing-1);
		}
	}

	.tab__button + .tab__button {
		border-radius: 0 var(--spacing-n1) var(--spacing-n1) 0;
		margin-left: -2px;
	}

	.tab__button--active {
		color: var(--color-secondary);
		background-color: var(--color-secondary-faded);
		position: relative;
		z-index: 2;
	}
</style>
