<script>
	import { createRadioGroup, melt } from '@melt-ui/svelte';

	const {
		elements: { root, item, hiddenInput },
		states: { value }
	} = createRadioGroup({
		defaultValue: 'option-1'
	});

	const options = [
		{ value: 'option-1', label: 'Option 1' },
		{ value: 'option-2', label: 'Option 2' },
		{ value: 'option-3', label: 'Option 3' }
	];

	$: console.log('Radio group value changed:', $value);
</script>

<div use:melt={$root} class="flex flex-col gap-3">
	{#each options as option}
		<div class="flex items-center gap-3">
			<button
				use:melt={$item(option.value)}
				class="hover:bg-magnum-100 grid h-6 w-6 cursor-default place-items-center rounded-full bg-white
            shadow-sm"
				id={option.value}
				aria-labelledby="{option.value}-label"
			>
				{#if $value === option.value}
					<div class="bg-magnum-500 h-3 w-3 rounded-full" />
				{/if}
			</button>
			<label
				class="text-magnum-900 font-medium capitalize leading-none"
				for={option.value}
				id="{option.value}-label"
			>
				{option.label}
			</label>
		</div>
	{/each}
	<input name="radio-group" use:melt={$hiddenInput} />
</div>
