<script>
	export let title = 'Test Container';
</script>

<div class="mx-auto max-w-[50%] rounded bg-gray-100 p-5">
	<h3 class="mb-5 text-2xl font-bold text-[#444]">{title}</h3>

	<div class="rounded-md bg-[#F7B155] px-5 py-10">
		<slot></slot>
	</div>
</div>
