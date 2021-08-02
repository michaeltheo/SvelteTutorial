<script>
	import Header from './components/Header.svelte';
	import Footer from './components/Footer.svelte';
	import PollList from './components/PollList.svelte';
	import Tabs from './shared/Tabs.svelte';
	import CreatePollForm from './components/CreatePollForm.svelte';
	
//tab
let items=['Current Polls','Add New Poll'];
let activeItem='Current Polls';
const tabChange=(e)=>{
	activeItem=e.detail;
}


const handleADD=(e)=>
{
	activeItem='Current Polls';
	console.log("go to Current polls");
}

import {tweened} from 'svelte/motion';
const value=tweened(0);
</script>

<button on:click={()=>value.set(1)}>{$value}</button>


<Header/>
<main>
	<Tabs {activeItem} {items} on:tabChange={tabChange}/>
	{#if activeItem==='Current Polls'}
	<PollList />
	{:else if activeItem==='Add New Poll'}
	<CreatePollForm on:add={handleADD}/>
	{/if}
</main>
<Footer/>

<style>
main{
	max-width: 960px;
	margin: 40px auto;
}
</style>

<!-- —(••÷[ 𝕗𝐑乇Ⓔ мⒾᛕε ]÷••)— -->