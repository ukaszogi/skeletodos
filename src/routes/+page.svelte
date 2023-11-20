<script lang="ts">
	let value = '';

	function handleKeydown(e: KeyboardEvent) {
		console.log(e);
		let element: HTMLInputElement = e.target; //śmieszny error, nic nie robi, wymieniłem dwa errory na jeden
		if (e.key == 'Enter') {
			console.log('No tu będzie dodawany todo z', element.value); //NIE WIEM CZEMU NIE DZIAŁA PO PROSTU value
			element.placeholder = 'Może więcej dozrobieniusów, co?';
			element.value = ''; //tu to samo
		}
	}

	$: console.log(value);
</script>

<div class="container h-full mx-auto flex justify-center items-center">
	<div class="space-y-5">
		<h2 class="h2">Czuj się wolny by dodać dozrobienia!</h2>
		<label class="label">
			Treść Twojej supermisji
			<input
				{value}
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
