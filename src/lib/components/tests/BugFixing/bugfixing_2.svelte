<script>
	import { createSlider, melt } from '@melt-ui/svelte';

	const {
		elements: { root, range, thumbs },
		states: { value }
	} = createSlider({
		defaultValue: [30],
		min: 0,
		max: 100,
		step: 1,
		onValueChange: handleValueChange
	});

	let doubledValue = 0;

	// function passed to onValueChange to update the doubledValue
	function handleValueChange(value) {
		doubledValue = value.next * 2;
		return value.next; // Return the new value to update the slider store
	}
</script>

<span> The chosen value is {$value}, while doubled: {doubledValue}</span>

<span use:melt={$root} class="relative flex h-[20px] w-[200px] items-center">
	<span class="h-[3px] w-full bg-black/40">
		<span use:melt={$range} class="h-[3px] bg-white" />
	</span>

	<span
		use:melt={$thumbs[0]}
		class="h-5 w-5 rounded-full bg-white focus:ring-4 focus:!ring-black/40"
	></span>
</span>
