<script>
	import Navbar from './Navbar.svelte'

	let header = "Ynte's Svelte App";
	let count = 0
	const increment = () => {
		count ++
	}
	const decrement = () => {
		count --
	}
	let newTask = ''
	let taskList = []

	function addTask() {
		taskList=[...taskList, {text: newTask, completed: false}]
		if (newTask.length < 1) {
			alert('Je moet wel iets invullen broer')
			return
		} else {
			return newTask = ''
		}
	}

	function deleteTask(index) {
		taskList.splice(index, 1)
		taskList = taskList
	}

	let randomNumber = 0

	function diceRoll(min, max) {
		min = Math.ceil(1);
   		max = Math.floor(6);
		randomNumber = Math.floor(Math.random() * (max-min) + min)
	}

</script>

<Navbar />

<h1>{header}!</h1>
<button on:click={increment}>Increment</button>
<button on:click={decrement}>Decrement</button>
<p>{count}</p>

<input bind:value={newTask} type="text" placeholder="wat moet je doen...">
<button on:click={addTask}>Add Task</button>
<br/>

{#each taskList as task, index}
<input bind:checked={task.completed} type="checkbox">
<span class:completed={task.completed}>{task.text}</span>
<span class=deleteBtn on:click={() => deleteTask(index)}>X</span>
<br/>
{/each}

<button on:click={diceRoll}>Roll Dice</button>
<p>{randomNumber}</p>

<style>
	h1 {
		color: darkgoldenrod;
	}
	.completed {
		text-decoration: line-through;
	}
	.deleteBtn {
		cursor:pointer;
		margin-left: 100px;
		border: 1px solid #ccc;
	}
</style>