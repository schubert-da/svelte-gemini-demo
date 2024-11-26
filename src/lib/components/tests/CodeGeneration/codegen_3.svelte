<script>
	import { createSelect, melt } from '@melt-ui/svelte';
	import { Check, ChevronDown } from 'lucide-svelte';
	import { writable } from 'svelte/store';

	const groups = [
		{
			key: 'fruits',
			label: 'Fruits',
			options: [
				{ value: 'apple', label: 'Apple', group: 'fruits' },
				{ value: 'banana', label: 'Banana', group: 'fruits' },
				{ value: 'orange', label: 'Orange', group: 'fruits' }
			]
		},
		{
			key: 'vegetables',
			label: 'Vegetables',
			options: [
				{ value: 'carrot', label: 'Carrot', group: 'vegetables' },
				{ value: 'broccoli', label: 'Broccoli', group: 'vegetables' },
				{ value: 'tomato', label: 'Tomato', group: 'vegetables' }
			]
		}
	];

	const selected = writable([]);

	const {
		elements: { trigger, label, menu, option, group: groupEl, groupLabel },
		states: { open },
		helpers: { isSelected }
	} = createSelect({
		multiple: true,
		selected,
		positioning: {
			placement: 'bottom',
			fitViewport: true,
			sameWidth: true
		}
	});

	function toggleGroup(groupKey) {
		selected.update((prev) => {
			const group = groups.find((g) => g.key === groupKey);
			if (!group) return prev;

			const isGroupSelected = prev.some((o) => o.group === groupKey);

			if (isGroupSelected) {
				return prev.filter((o) => o.group !== groupKey);
			} else {
				return [...prev, ...group.options];
			}
		});
	}
</script>

<div class="flex flex-col gap-1">
	<!-- svelte-ignore a11y-label-has-associated-control - $label contains the 'for' attribute -->
	<label class="block text-magnum-900" use:melt={$label}> Select your favorite items: </label>
	<button
		class="flex h-10 min-w-[220px] items-center justify-between rounded-lg bg-white px-3 py-2
    text-magnum-700 shadow transition-opacity hover:opacity-90"
		use:melt={$trigger}
		aria-label="Food"
	>
		{$selected.length > 0 ? $selected.map((o) => o.label).join(', ') : 'Select an option'}
		<ChevronDown class="size-5" />
	</button>
	{#if $open}
		<div
			class="force-dark z-10 flex max-h-[300px] flex-col
        overflow-y-auto rounded-lg bg-white p-1
        shadow focus:!ring-0"
			use:melt={$menu}
		>
			{#each groups as group}
				<div use:melt={$groupEl(group.key)}>
					<div
						class="py-1 pl-4 pr-4 font-semibold capitalize text-neutral-800"
						use:melt={$groupLabel(group.key)}
						on:click={() => toggleGroup(group.key)}
					>
						{group.label}
					</div>
					{#each group.options as opt}
						<div class="" use:melt={$option(opt)}>
							{#if $isSelected(opt)}
								<div class="check absolute left-2 top-1/2 z-10 text-magnum-900">
									<Check class="size-4" />
								</div>
							{/if}

							{opt.label}
						</div>
					{/each}
				</div>
			{/each}
		</div>
	{/if}
</div>

<style lang="postcss">
	.check {
		position: absolute;
		left: theme(spacing.2);
		top: 50%;
		z-index: theme(zIndex.20);
		translate: 0 calc(-50% + 1px);
		color: theme(colors.magnum.500);
	}
</style>
