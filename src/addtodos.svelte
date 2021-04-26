<script>
let headertext="";
let bodytext="";
import { createEventDispatcher } from 'svelte';
const dispatch = createEventDispatcher();
function submitform(e){
	e.preventDefault()
		dispatch('addtodo', {
			header: headertext,
			body:bodytext
		});
	headertext="";
	bodytext="";
	}
</script>
<form class="container" on:submit={submitform}>
	<input bind:value={headertext}/>
<input  bind:value={bodytext}/>
<input type="submit" value="Add" />
</form>