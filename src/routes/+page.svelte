<script lang="ts">
	let todo_task = '';
	let todos = {
		
	}

	function handleKeydown(e: KeyboardEvent) {
		// console.log(e, todo_task);
		let element: HTMLInputElement = e.target; //śmieszny error, nic nie robi, wymieniłem dwa errory na jeden
		if (e.key == 'Enter') {
			console.log('No tu będzie dodawany todo z', todo_task); //już wiem jak naprawić, ale nadal nie wiem czemu
			element.placeholder = 'Może więcej dozrobieniusów, co?';
			todo_task = ''; //trzeba było nie używać skróconej formy do input:text jako {value}
		}
	}

	// $: console.log(todo_task);
</script>

<div class="container h-full mx-auto flex justify-center items-center">
	<div class="space-y-5">
		<h2 class="h2">Czuj się wolny by dodać dozrobienia!</h2>
		<label class="label">
			Treść Twojej supermisji
			<input
				bind:value={todo_task}
				on:keydown={handleKeydown}
				class="input"
				type="text"
				name="content"
				id="content-input"
				placeholder="Dodaj dozrobienia bracie"
			/>
		</label>
	</div>
</div>
