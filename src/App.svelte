<script>
	import Draggable from './Draggable.svelte';
	let header = 'Notitie Buddy'
	let note = ''
	let noteList = []

	const addNote = () => {
		noteList = [...noteList, {text: note, completed: false}]
	}

	const deleteNote = (index) => {
		noteList.splice(index, 1)
		noteList = noteList
	}

</script>

<div class="noteForm">
<h1>{header}</h1>
<input bind:value={note} type="text" placeholder='Typ hier een notitie in...' />
<button class="addBtn" on:click={addNote}>Notitie toevoegen</button>
</div>

{#each noteList as note, index}


<Draggable><div class:note><input bind:checked={note.completed} type="checkbox" /><button class="delBtn" on:click={() => deleteNote(index)}>X</button><span class:completed={note.completed}>{note.text}</span></div></Draggable>



{/each}

<style>
	h1 {
		font-weight: bold;
	}
	.note {
		width: 100px;
		height: 100px;
		background: #feff9c;
		font-size: 2em;
		color: black;
		text-align: justify;
	}

	.completed {
		text-decoration: line-through;
	}

	.noteForm {
		position: static;
		display: grid;
		place-content: center;
	} 
	.addBtn {
		background: aliceblue;
		border-style: none;
		border-radius: 3%;
		height: 40px;
		cursor: pointer;
		font-size: 1em;
		color: #001f3f;
	}

	.addBtn:hover {
		opacity: 90%;
	}

	.delBtn {
		background: none;
		border-style: none;
		cursor: pointer;
	}

</style>
