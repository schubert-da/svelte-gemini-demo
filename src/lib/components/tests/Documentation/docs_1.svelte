<script lang="ts">
	import { createAccordion, melt } from '@melt-ui/svelte';

	const someCondition = false;

	const {
		elements: { content, item, trigger, root },
		options: { disabled },
		states: { value }
	} = createAccordion({
		onValueChange: ({ curr, next }) => {
			if (next === 'item-3' && !someCondition) {
				return curr;
			}
			return next;
		}
	});
</script>

<button
	on:click={() => {
		const randPick = Math.floor(Math.random() * 3) + 1;
		value.set(`item-${randPick}`);
		// Alternatively, you can use the value store directly value.set(`item-${randPick}`)
	}}
>
	Trigger randomly
</button>

<p>Value: {$value}</p>

<div use:melt={$root}>
	<div use:melt={$item('item-1')}>
		<button use:melt={$trigger('item-1')}>Is it accessible?</button>
		<div use:melt={$content('item-1')}>
			<div>Yes. It adheres to the WAI-ARIA design pattern.</div>
		</div>
	</div>

	<div use:melt={$item('item-2')}>
		<button use:melt={$trigger('item-2')}>Is it accessible?</button>
		<div use:melt={$content('item-2')}>
			<div>Yes. It adheres to the WAI-ARIA design pattern.</div>
		</div>
	</div>

	<div use:melt={$item('item-3')}>
		<button use:melt={$trigger('item-3')}>Is it accessible?</button>
		<div use:melt={$content('item-3')}>
			<div>Yes. It adheres to the WAI-ARIA design pattern.</div>
		</div>
	</div>
</div>
