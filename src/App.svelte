<script>
import Header from "./components/Header.svelte";
import Footer from "./components/Footer.svelte";
import Tabs from "./shared/Tabs.svelte";
import CreatePollForm from "./components/CreatePollForm.svelte";
import PollList from "./components/PollList.svelte";

//tabs
let items=['Current Polls','Add New Poll'];
let activeItem='Current Polls';

let polls=[
	{id:1,question:'Python or Javascript?',answerA:'Python',answerB:'Javascript',votesA:9,votesB:15}
];

//Handling tab change
const handleTabsChange=(e)=>{
	activeItem=e.detail;
}

//Handling new poll data
const handleAddPoll=(e)=>{
	// const poll= e.detail;
	// polls=[poll,...polls];
	activeItem='Current Polls';
}

//Handling vote
// const handleVote =(e)=> {
// 	const {option,id} = e.detail;
//
// 	let copiedPolls =[...polls];
// 	let upVotedPoll = copiedPolls.find((poll)=>poll.id===id);
// 	if(option==='a'){
// 		upVotedPoll.votesA++;
// 	}else{
// 		upVotedPoll.votesB++;
// 	}
// 	polls=copiedPolls;
// }
</script>


<div>
	<Header/>
	<main>
		<Tabs {activeItem} {items} on:tabChange={handleTabsChange}/>

		{#if activeItem==='Current Polls'}
<!--			<PollList  on:vote={handleVote}/>-->
			<PollList/>
		{:else if activeItem==='Add New Poll'}
			<CreatePollForm on:addPoll={handleAddPoll}/>
		{/if}


	</main>
	<Footer/>
</div>

<style>
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style>