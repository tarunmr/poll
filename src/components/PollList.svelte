<script>
    // import {onMount,onDestroy} from 'svelte';
    import PollDetails from "./PollDetails.svelte";
    import PollStore from "../stores/PollStore";
    import {fade,scale,slide} from 'svelte/transition';
    import {flip} from 'svelte/animate';

    // export let polls=[];
    //
    // const unsub=PollStore.subscribe(data=>{polls=data});
    //
    // onMount(()=>{
    //     // may be get data from db
    //     console.log('Component Mounted');
    // })
    //
    // onDestroy(()=>{
    //     //    unsub from store
    //     unsub();
    // })


</script>

<div class="poll-list">
    {#each $PollStore as poll (poll.id)}
        <div in:fade out:slide|local animate:flip={{duration:500}}>
            <PollDetails {poll}/>
        </div>
        {:else}
        <div>No polls to display</div>
     {/each}
</div>

<style>
.poll-list{
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
}
</style>