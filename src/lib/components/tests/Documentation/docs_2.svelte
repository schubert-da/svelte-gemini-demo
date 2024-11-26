<script lang="ts" context="module">
	export type ToastData = {
		title: string;
		description: string;
		color: string;
	};

	const {
		elements: { content, title, description, close },
		helpers,
		states: { toasts },
		actions: { portal }
	} = createToaster<ToastData>();

	export const addToast = helpers.addToast;

	import { createToaster, melt } from '@melt-ui/svelte';
</script>

<div use:portal>
	{#each $toasts as { id, data } (id)}
		<div use:melt={$content(id)} class="toast">
			<div>
				<div>
					<h3 use:melt={$title(id)}>
						{data.title}
						<span style:color={data.color}></span>
					</h3>
					<div use:melt={$description(id)}>
						{data.description}
					</div>
				</div>
				<button use:melt={$close(id)} aria-label="close notification"> X </button>
			</div>
		</div>
	{/each}
</div>

<style>
	.toast {
		position: fixed;
		top: 1rem;
		right: 1rem;
		background-color: #333;
		color: white;
		padding: 1rem;
		border-radius: 4px;
		box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
	}
</style>
