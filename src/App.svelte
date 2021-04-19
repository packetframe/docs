<script>
	import Router from 'svelte-spa-router';
	import MDPWrapper from 'rollup-plugin-mdsvex-pages/src/components/MDPWrapper.svelte';

	const routes = {};
</script>

<MDPWrapper styles={{}}>
	<main>
		<Router {routes} />
	</main>
</MDPWrapper>
