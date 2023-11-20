<script lang="ts">
	let todo_task = '';
	let todos = [
    {
      id: 0,
      todo_task: "Helena",
      todo_done: false,
      created_date: new Date()
    },
    {
      id: 1,
      todo_task: "Obsraj spodnie",
      todo_done: true,
      created_date: new Date()
    }
	]

	function add_todo(e: KeyboardEvent) {
		// console.log(e, todo_task);
		const element: HTMLInputElement = e.target; //śmieszny error, nic nie robi, wymieniłem dwa errory na jeden
		if (e.key == 'Enter') {
			// console.log('No tu będzie dodawany todo z', todo_task);
      todos = [{
        id: window.crypto.randomUUID(),
        todo_task: todo_task,
        todo_done: false,
        created_date: new Date()
      }, ...todos]
			element.placeholder = 'Może więcej dozrobieniusów, co?';
			todo_task = '';
		}
	}


</script>

<div class="container h-full mx-auto flex justify-center items-center">
	<div class="space-y-5">
		<h2 class="h2">Czuj się wolny by dodać dozrobienia!</h2>
		<label class="label">
			Treść Twojej supermisji (supremacji Twojego chłopaka)
			<input
				bind:value={todo_task}
				on:keydown={add_todo}
				class="input w-50"
				type="text"
				name="content"
				id="content-input"
				placeholder="Dodaj dozrobienia bracie"
			/>
		</label>
    {#each todos as todo}
      <input 
        class="input w-50 {todo.todo_done ? 'variant-soft-success' : 'variant-soft-error'}"
        value={todo.todo_task} 
      />
    {/each}
	</div>
</div>
