<script>

    import { web, account } from "../lib/web";

    const truncate = (input, length = 6) => input.length > length ? `${input.substring(0, length)}...` : input;

    $: text = 
        $web.isConnected ? truncate($account?.address) :
        'connect'
</script>


<div class="">
    <button 
    class="bg-blue-500 text-white px-5 py-2 rounded-lg transition-all  hover:scale-105 hover:bg-blue-400"
    on:click={$web.connect}>{text}</button>
</div>