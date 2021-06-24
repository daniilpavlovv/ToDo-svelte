<script>
	import Field from '../components/Field.svelte';
	import Task from '../components/Task.svelte';

	let tasks = [];

	const onAddTask = (text) => {
		tasks = [
			{
				text,
				completed: false
			},
			...tasks
		];
	};

	const onToggleCompleted = (index) => {
		tasks[index].completed = !tasks[index].completed;
	};

	const onRemoveTasks = (index) => {
		tasks = tasks.filter((_, curIdx) => index !== curIdx);
	};
</script>

<div class="todo">
	<header class="todo__header">
		<h1 class="todo__header-title">ToDo list</h1>
	</header>
	<main class="todo__main">
		<Field {onAddTask} />
		<div class="todo__tasks">
			{#each tasks as task, index}
				<Task
					{index}
					text={task.text}
					completed={task.completed}
					{onToggleCompleted}
					{onRemoveTasks}
				/>
			{/each}
		</div>
	</main>
</div>

<style global>
	@import '../styles/css/style.css';
</style>
