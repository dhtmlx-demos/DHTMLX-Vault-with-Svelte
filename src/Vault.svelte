<script>
    import { onMount } from "svelte";
    
    import { Vault } from "@dhx/trial-vault";
    import "@dhx/trial-vault/codebase/vault.min.css";
    
    export let files;

    let container;
    let vault;
    onMount(() => {
        vault = new Vault(container,{
            uploader: {
                target: "https://docs.dhtmlx.com/vault/backend/upload"
            },
            downloadURL: "https://docs.dhtmlx.com"
        });
        return () => vault.destructor();
    });

    $: vault?.data.parse(files)
</script>

<div bind:this={container} class="container"></div>

<style>
    .container {
        width: 440px;
        height: 400px;
        margin: 50px auto;
    }
</style>