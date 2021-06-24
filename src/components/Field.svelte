<script>
	export let onAddTask;

	let text = '';

	const addTask = () => {
		if (text) {
			onAddTask(text);
			text = '';
		}
	};
</script>

<div class="todo__main__add-field">
	<input
		bind:value={text}
		class="todo__main__add-field-input"
		type="text"
		placeholder="Enter task"
	/>
	<button on:click={addTask} class="button button-add">
		<span class="ripple" />
		<svg height="24" width="24">
			<path fill="none" d="M0 0h24v24H0z" />
			<path d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2z" />
		</svg>
	</button>
</div>
