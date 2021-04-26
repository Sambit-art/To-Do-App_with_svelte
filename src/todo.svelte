<script>
	export let header;
	export let body;
	export let id;
	let editmode=false
	import { createEventDispatcher } from 'svelte';
const dispatch = createEventDispatcher();
function editbtn(){
	editmode=!editmode
}
	function deletebtn(){
	dispatch('deletetodo', {
			id:id
		});
}
</script>
	
<style>
	.item_id{
		padding: 2px 10px;
		border-radius: 50%;
	}
</style>

<div class="col s6">
      <div class="card teal lighten-3">
        <div class="card-content white-text">
          <span class="card-title">
          <span class=" teal darken-3 item_id">{id}</span>

          {header}</span>
         <h4>{body}</h4>
         {#if editmode}
          		<input bind:value={header}/>
          		<input bind:value={body}/>
          	{/if}
        </div>
        <div class="card-action">
          	{#if editmode}
          		<button class="waves-effect waves-light btn   brown darken-3" on:click={editbtn}>Update</button>
          	{:else}
          		<button class="waves-effect waves-light btn indigo darken-2" on:click={editbtn}>Edit</button>
          	{/if}
      
			<button class="waves-effect waves-light btn red darken-2" on:click={deletebtn}>Delete</button>
        </div>
      </div>
    </div>