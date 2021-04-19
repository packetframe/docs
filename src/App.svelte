<script>
	import Router, {replace, location} from "svelte-spa-router";
	import MDPWrapper from "rollup-plugin-mdsvex-pages/src/components/MDPWrapper.svelte";
	import Redir from "./Redir.svelte";

	const routes = {"*": Redir};

	if ($location === "/") {
		replace("/docs");
	}
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
