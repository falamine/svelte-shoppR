<script lang="ts">
	import {fly} from 'svelte/transition'
	let newTask = '';
	let hideDone = false;
	let list = [
		{title: 'task1', isDone: false}
	];
	
	function onAddNew() {
		list = [...list, {title: newTask, isDone: false}]
	}
	
	$: sortedList = list.sort((a,b) => a.isDone - b.isDone).filter(i => !i.isDone || !hideDone)
</script>

<style>
	button { color: red }
</style>

<div>
	<input bind:value={newTask}>
	<button on:click={onAddNew}>
		Add New
	</button>
</div>
<div>
	<label><input type="checkbox" bind:checked={hideDone}> Hide Done?</label>
</div>
<hr>
{#each sortedList as item}
	<div in:fly={{y: -10}} out:fly={{x: 10}}>
		<label>
			<input type="checkbox" bind:checked={item.isDone}> 
			<span style="text-decoration: {item.isDone? 'line-through':'none'}">{item.title}</span>
		</label>
</div>
{/each}