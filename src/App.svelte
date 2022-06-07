<script>
    import ConnectButton from "./comp/ConnectButton.svelte";
    import Gallery from "./comp/Gallery.svelte";
    
    // @ts-ignore
    $: kaikasSupport = window?.klaytn;

    import {} from './lib/web';


</script>

<main class="">
    {#if !kaikasSupport}
        <div class="flex justify-center items-center w-screen h-screen">
            <p> 
                please install 
                <a class="inline-block underline text-sky-600 hover:animate-pulse" 
                href="https://chrome.google.com/webstore/detail/kaikas/jblndlipeogpafnldhgmapagcccfchpi"
                target=_blank>kaikas</a> 
                (chrome only)
            </p>
        </div>
    {:else}
        <div class="w-screen h-screen">
            <div class="absolute right-5 top-5">
                <ConnectButton></ConnectButton>
            </div>
            <Gallery></Gallery>
        </div>
    {/if}
</main>

<style>

</style>