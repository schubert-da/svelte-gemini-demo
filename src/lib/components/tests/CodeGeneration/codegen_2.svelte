<!-- You really don't need to read this code - I'll summarise my findings right after -->
<!-- Dropdown.svelte -->
<script>
	import { Dropdown, DropdownTrigger, DropdownContent, DropdownItem } from '@melt-ui/svelte';
	import { onMount } from 'svelte';

	let selectedOption = 'Select an option';

	const options = [
		{ id: 1, label: 'Option 1' },
		{ id: 2, label: 'Option 2' },
		{ id: 3, label: 'Option 3' }
	];

	function handleSelect(option) {
		selectedOption = option.label;
	}
</script>

<Dropdown>
	<DropdownTrigger class="cursor-pointer rounded-md bg-gray-200 px-4 py-2">
		{selectedOption}
	</DropdownTrigger>

	<DropdownContent class="mt-2 rounded-md border border-gray-300 bg-white shadow-lg">
		{#each options as option}
			<DropdownItem
				on:click={() => handleSelect(option)}
				class="cursor-pointer px-4 py-2 hover:bg-gray-100"
			>
				{option.label}
			</DropdownItem>
		{/each}
	</DropdownContent>
</Dropdown>
