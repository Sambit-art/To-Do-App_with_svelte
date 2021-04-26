<script>
import Todo from './todo.svelte';
import Addtodos from './addtodos.svelte';
let todos=[{id:1,header:'go to code',body: "learn svelte"},{id:2,header:'go to market',body: "Buy Mangoes"}]
function addnewtodo(e){
	let new_item=e.detail
	new_item.id=parseInt(todos.length)+1
	console.log(new_item)
	todos=[...todos,e.detail]
}
function deletetodo(e){
	let id_to_delete=e.detail.id
	let newitem=todos.filter(item=>item.id!=id_to_delete)
	todos=newitem
}
</script>
<Addtodos on:addtodo={addnewtodo} />
<div class="row container">
{#each todos as { header, body,id }}
	<Todo {header} {body} {id} on:deletetodo={deletetodo}/>
{/each}
</div>