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

//polls
let polls=[
	{
		id:1,
		question:'Python or Javascript',
		answearA: 'Python',
		answearB: 'Javascript',
		votesA:9,
		votesB:15,
	},
];

const handleADD=(e)=>
{
	const poll=e.detail;
	polls=[poll,...polls];
	console.log(polls);
	activeItem='Current Polls'
}

</script>


<Header/>
<main>
	<Tabs {activeItem} {items} on:tabChange={tabChange}/>
	{#if activeItem==='Current Polls'}
	<PollList  polls={polls} />
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