<script>
    import { onMount } from "svelte";
    import {web } from '../lib/web';

    let id = 1;
    let uri = "";

    $: src = uri.replace("json/{id}.json", `images/${id.toString()}.png`);

    onMount(async () => {
        uri = await $web.getUri();
    });

</script>

<div class="w-screen h-screen flex flex-col items-center gap-10 justify-center">

    <div class="flex items-center justify-center gap-5">
        {#if uri}
            <!-- <img class="shadow-2xl w-1/4" src={getSrc(wrap(id-1, 1, 28))} alt="an l-system"> -->
            <img class="shadow-2xl w-1/2" {src} alt="an l-system">
            <!-- <img class="shadow-2xl w-1/4" src={getSrc(wrap(id+1, 1, 28))} alt="an l-system"> -->
        {:else}
            <div class="w-10 h-1 bg-black rounded-lg animate-spin"></div>
        {/if}
    </div>
    <button 
    on:click={() => $web.mint(id)}
    class="w-max text-white px-5 py-2 rounded-lg bg-emerald-500 hover:scale-105 transition-transform"> mint </button>
    
</div>