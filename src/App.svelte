<script>
	import Router from 'svelte-spa-router';
	import MDPWrapper from 'rollup-plugin-mdsvex-pages/src/components/MDPWrapper.svelte';

	const routes = {};
</script>

<MDPWrapper styles={{
	"text-color": "white",
	"background-color": "black",
	"sidebar-active": "#2b2b2b",
	"sidebar-hover": "#2b2b2b",
	"content-sidebar-padding": "30px"
}}>
	<main>
		<Router {routes} />
	</main>
</MDPWrapper>
