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
}

const handleVote=(e)=>
{
	const {id,option}=e.detail;
	let copiedPolls=[...polls];
	let upvotedPoll=copiedPolls.find((poll)=>poll.id==id);

	if(option === 'a'){
		upvotedPoll.votesA++;
	}
	if(option === 'b'){
		upvotedPoll.votesB++;
	}
	polls=copiedPolls;
}

</script>


<Header/>
<main>
	<Tabs {activeItem} {items} on:tabChange={tabChange}/>
	{#if activeItem==='Current Polls'}
	<PollList   on:vote={handleVote}/>
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