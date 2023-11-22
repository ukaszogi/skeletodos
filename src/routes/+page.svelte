<script lang="ts">
	let task = '';
	let todos = [
    {
      id: 0,
      task: "Helena",
      done: false,
      created_date: new Date()
    },
    {
      id: 1,
      task: "Obsraj spodnie",
      done: true,
      created_date: new Date()
    }
	]

	function add_todo(e: KeyboardEvent) {
		// console.log(e, task);
		const element: HTMLInputElement = e.target; //śmieszny error, nic nie robi, wymieniłem dwa errory na jeden
		if (e.key == 'Enter') {
			// console.log('No tu będzie dodawany todo z', task);
      todos = [{
        id: window.crypto.randomUUID(),
        task,
        done: false,
        created_date: new Date()
      }, ...todos]
			element.placeholder = 'Może więcej dozrobieniusów, co?';
			task = '';
		}
	}

</script>

<div class="container h-full mx-auto flex flex-col p-4 gap-4 items-center">
  <h2 class="h2">Czuj się wolny by dodać dozrobienia!</h2>
  <label class="label flex flex-col w-2/3">
    Treść Twojej supermisji (supremacji Twojego chłopaka)
    <input
      bind:value={task}
      on:keydown={add_todo}
      class="input"
      type="text"
      name="content"
      id="content-input"
      placeholder="Dodaj dozrobienia bracie"
    />
  </label>
  {#each todos as todo (todo.id)}
    <div class="card p-2 px-3 w-2/3  flex justify-start gap-4 content-center items-center">
      <input type="checkbox" class="checkbox" bind:checked={todo.done}/>
      <span>{todo.task}</span>
    </div>
  {/each}
</div>
