<script lang="ts">
	import { createTreeView, melt } from '@melt-ui/svelte';
	import { Folder, FolderOpen } from 'lucide-svelte';

	type TreeItem = {
		title: string;
		icon: 'folder' | 'folderOpen';
		children?: TreeItem[];
	};

	const treeItems: TreeItem[] = [
		{
			title: 'Phylum Chordata',
			icon: 'folder',
			children: [
				{
					title: 'Class Chondrichthyes',
					icon: 'folder',
					children: [
						{
							title: 'Order Selachimorpha',
							icon: 'folder',
							children: [
								{
									title: 'Family Carcharhinidae',
									icon: 'folder',
									children: [
										{
											title: 'Examples',
											icon: 'folderOpen',
											children: [
												{ title: 'Blacktip Reef Shark', icon: 'folderOpen' },
												{ title: 'Bull Shark', icon: 'folderOpen' },
												{ title: 'Caribbean Reef Shark', icon: 'folderOpen' },
												{ title: 'Lemon Shark', icon: 'folderOpen' },
												{ title: 'Nurse Shark', icon: 'folderOpen' },
												{ title: 'Sandbar Shark', icon: 'folderOpen' },
												{ title: 'Silky Shark', icon: 'folderOpen' },
												{ title: 'Tiger Shark', icon: 'folderOpen' },
												{ title: 'Whitetip Reef Shark', icon: 'folderOpen' }
											]
										}
									]
								},
								{
									title: 'Family Scyliorhinidae',
									icon: 'folder',
									children: [
										{
											title: 'Examples',
											icon: 'folderOpen',
											children: [
												{ title: 'Catshark', icon: 'folderOpen' },
												{ title: 'Chain Catshark', icon: 'folderOpen' },
												{ title: 'Whitespotted Bamboo Shark', icon: 'folderOpen' }
											]
										}
									]
								},
								{
									title: 'Family Sphyrnidae',
									icon: 'folder',
									children: [
										{
											title: 'Examples',
											icon: 'folderOpen',
											children: [
												{ title: 'Bonnethead Shark', icon: 'folderOpen' },
												{ title: 'Great Hammerhead', icon: 'folderOpen' },
												{ title: 'Scalloped Hammerhead', icon: 'folderOpen' }
											]
										}
									]
								}
							]
						},
						{
							title: 'Order Rajiformes',
							icon: 'folder',
							children: [
								{
									title: 'Family Rhinobatidae',
									icon: 'folder',
									children: [
										{
											title: 'Examples',
											icon: 'folderOpen',
											children: [
												{ title: 'White-spotted Shovelnose Ray', icon: 'folderOpen' },
												{ title: 'Fanray', icon: 'folderOpen' },
												{ title: 'Shovelnose Ray', icon: 'folderOpen' }
											]
										}
									]
								},
								{
									title: 'Family Rajidae',
									icon: 'folder',
									children: [
										{
											title: 'Examples',
											icon: 'folderOpen',
											children: [
												{ title: 'Thorny Skate', icon: 'folderOpen' },
												{ title: 'Winter Skate', icon: 'folderOpen' },
												{ title: 'Big Skate', icon: 'folderOpen' }
											]
										}
									]
								}
							]
						}
					]
				},
				{
					title: 'Class Actinopterygii',
					icon: 'folder',
					children: [
						{
							title: 'Order Perciformes',
							icon: 'folder',
							children: [
								{
									title: 'Family Serranidae',
									icon: 'folder',
									children: [
										{
											title: 'Examples',
											icon: 'folderOpen',
											children: [
												{ title: 'Grouper', icon: 'folderOpen' },
												{ title: 'Sea Bass', icon: 'folderOpen' },
												{ title: 'Rockfish', icon: 'folderOpen' }
											]
										}
									]
								},
								{
									title: 'Family Carangidae',
									icon: 'folder',
									children: [
										{
											title: 'Examples',
											icon: 'folderOpen',
											children: [
												{ title: 'Jack', icon: 'folderOpen' },
												{ title: 'Mahi-mahi', icon: 'folderOpen' },
												{ title: 'Amberjack', icon: 'folderOpen' }
											]
										}
									]
								},
								{
									title: 'Family Scombridae',
									icon: 'folder',
									children: [
										{
											title: 'Examples',
											icon: 'folderOpen',
											children: [
												{ title: 'Tuna', icon: 'folderOpen' },
												{ title: 'Mackerel', icon: 'folderOpen' },
												{ title: 'Bonito', icon: 'folderOpen' }
											]
										}
									]
								}
							]
						},
						{
							title: 'Order Tetraodontiformes',
							icon: 'folder',
							children: [
								{
									title: 'Family Tetraodontidae',
									icon: 'folder',
									children: [
										{
											title: 'Examples',
											icon: 'folderOpen',
											children: [
												{ title: 'Pufferfish', icon: 'folderOpen' },
												{ title: 'Porcupinefish', icon: 'folderOpen' },
												{ title: 'Boxfish', icon: 'folderOpen' }
											]
										}
									]
								}
							]
						}
					]
				}
			]
		},
		{
			title: 'Phylum Mollusca',
			icon: 'folder',
			children: [
				{
					title: 'Class Cephalopoda',
					icon: 'folder',
					children: [
						{
							title: 'Order Octopoda',
							icon: 'folder',
							children: [
								{
									title: 'Family Octopodidae',
									icon: 'folder',
									children: [
										{
											title: 'Examples',
											icon: 'folderOpen',
											children: [
												{ title: 'Common Octopus', icon: 'folderOpen' },
												{ title: 'Giant Pacific Octopus', icon: 'folderOpen' },
												{ title: 'Mimic Octopus', icon: 'folderOpen' }
											]
										}
									]
								}
							]
						},
						{
							title: 'Order Teuthida',
							icon: 'folder',
							children: [
								{
									title: 'Family Ommastrephidae',
									icon: 'folder',
									children: [
										{
											title: 'Examples',
											icon: 'folderOpen',
											children: [
												{ title: 'Humboldt Squid', icon: 'folderOpen' },
												{ title: 'Flying Squid', icon: 'folderOpen' },
												{ title: 'Diamondback Squid', icon: 'folderOpen' }
											]
										}
									]
								}
							]
						}
					]
				},
				{
					title: 'Class Gastropoda',
					icon: 'folder',
					children: [
						{
							title: 'Order Nudibranchia',
							icon: 'folder',
							children: [
								{
									title: 'Family Chromodorididae',
									icon: 'folder',
									children: [
										{
											title: 'Examples',
											icon: 'folderOpen',
											children: [
												{ title: 'Spanish Dancer', icon: 'folderOpen' },
												{ title: 'Blue Dragon', icon: 'folderOpen' },
												{ title: 'Chromodoris lochi', icon: 'folderOpen' }
											]
										}
									]
								}
							]
						}
					]
				}
			]
		},
		{
			title: 'Phylum Echinodermata',
			icon: 'folder',
			children: [
				{
					title: 'Class Asteroidea',
					icon: 'folder',
					children: [
						{
							title: 'Order Valvatida',
							icon: 'folder',
							children: [
								{
									title: 'Family Asteriidae',
									icon: 'folder',
									children: [
										{
											title: 'Examples',
											icon: 'folderOpen',
											children: [
												{ title: 'Common Starfish', icon: 'folderOpen' },
												{ title: 'Northern Sea Star', icon: 'folderOpen' },
												{ title: 'Spiny Starfish', icon: 'folderOpen' }
											]
										}
									]
								}
							]
						}
					]
				}
			]
		}
	];

	const {
		elements: { tree, item, group },
		helpers: { isExpanded }
	} = createTreeView({
		defaultExpanded: ['Phylum Chordata', 'Class Chondrichthyes', 'Order Selachimorpha']
	});
</script>

<div
	class="flex h-[30rem] w-[30rem] flex-col rounded-xl bg-white text-neutral-900 md:h-[350px]"
	use:melt={$tree}
>
	<div class="flex flex-col gap-1 px-4 pt-4">
		<h3 class="text-lg font-bold">Marine Animal Taxonomy</h3>
		<hr />
	</div>

	<ul class="overflow-auto px-4 pb-4 pt-2" use:melt={$tree}>
		<svelte:self {treeItems} />
	</ul>
</div>

<style lang="postcss">
	ul {
		@apply m-0 list-none;
	}

	li {
		@apply mt-0 pt-2;
	}

	button {
		@apply flex items-center gap-1 rounded-md p-1 focus:bg-magnum-200;
	}

	button > span {
		@apply select-none;
	}

	button > .lucide-folder {
		@apply h-4 w-4;
	}

	button > .lucide-folder-open {
		@apply h-4 w-4;
	}

	button > .lucide-arrow-left {
		@apply h-4 w-4;
	}

	ul {
		@apply m-0 list-none;
	}

	li {
		@apply mt-0 pt-2;
	}

	button {
		@apply flex items-center gap-1 rounded-md p-1 focus:bg-magnum-200;
	}

	button > span {
		@apply select-none;
	}

	button > .lucide-folder {
		@apply h-4 w-4;
	}

	button > .lucide-folder-open {
		@apply h-4 w-4;
	}

	button > .lucide-arrow-left {
		@apply h-4 w-4;
	}

	ul {
		@apply m-0 list-none;
	}

	li {
		@apply mt-0 pt-2;
	}

	button {
		@apply flex items-center gap-1 rounded-md p-1 focus:bg-magnum-200;
	}

	button > span {
		@apply select-none;
	}

	button > .lucide-folder {
		@apply h-4 w-4;
	}

	button > .lucide-folder-open {
		@apply h-4 w-4;
	}

	button > .lucide-arrow-left {
		@apply h-4 w-4;
	}
</style>
