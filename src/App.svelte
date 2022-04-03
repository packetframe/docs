<script>
    import Router from "svelte-spa-router";
    import MDPWrapper from "rollup-plugin-mdsvex-pages/src/components/MDPWrapper.svelte";
    import Redir from "./Redir.svelte";

    const routes = {"*": Redir};
</script>

<MDPWrapper styles={{
	"text-color": "white",
	"background-color": "black",
	"sidebar-active": "#2b2b2b",
	"sidebar-hover": "#2b2b2b",
	"content-sidebar-padding": "30px"
}}>
    <main>
        <Router {routes}/>
        <footer>
            &copy; Packetframe 2022
        </footer>
    </main>
</MDPWrapper>

<style>
    footer {
        color: white;
        text-align: center;
        padding: 15px;
    }
</style>
