<script>
	import TestContainer from '$lib/components/TestContainer/TestContainer.svelte';

	// CODE GENERATION
	import CodeGen_1 from '$lib/components/tests/CodeGeneration/codegen_1.svelte';
	// import Codegen_2 from '$lib/components/tests/CodeGeneration/codegen_2.svelte';
	import Codegen_3 from '$lib/components/tests/CodeGeneration/codegen_3.svelte';
	import Codegen_4 from '$lib/components/tests/CodeGeneration/codegen_4.svelte';

	// BUG FIXING
	import Bugfixing_1 from '$lib/components/tests/BugFixing/bugfixing_1.svelte';
	import Bugfixing_2 from '$lib/components/tests/BugFixing/bugfixing_2.svelte';

	// DOCUMENTATION
	import Docs_1 from '$lib/components/tests/Documentation/docs_1.svelte';
	import Docs_2 from '$lib/components/tests/Documentation/docs_2.svelte';
</script>

<TestContainer title="Toast Example">
	<Docs_2 />
</TestContainer>
