<script>
    import {location, replace} from "svelte-spa-router";

    if ($location === "/") {
        replace("/docs");
    } else {
        window.location = "https://packetframe.com/#/404";
    }
</script>
