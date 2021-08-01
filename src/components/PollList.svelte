<script>
//import { onDestroy, onMount } from 'svelte';
import PollStore from '../Stores/PollStore.js';
import PollDetails from './PollDetails.svelte';

//export let polls=[];
// const unsub = PollStore.subscribe(data => { 
// polls=data;
// });

// onDestroy(()=> {
// unsub();
// });




</script>


<div class="poll-list">
    {#each $PollStore  as poll (poll.id) }
    <div>
        <PollDetails {poll} on:vote  />
    </div>
    {/each}
</div>



<style>
    .poll-list{
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap:20px;
    }
</style>