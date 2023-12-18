<script>
	import CardBoy from './CardBoy.svelte';

	export let selectedBoy;
	export let data;

	export let search;

	$: {
		const found = data.find(({ name }) => name === search);
		if (found) {
			selectedBoy = found;
		} else {
			selectedBoy = {
				name: '',
				tally: 0
			};
		}
	}

	$: console.log(selectedBoy);
</script>

<div class="w-full h-full flex flex-col gap-4">
	<div class="h-[110px] bg-gray-900 rounded-2xl p-4">
		<label class="flex flex-col gap-2">
			Searcher:
			<input type="text" list="boys"
				   class="bg-gray-800 p-2 rounded outline-0"
				   placeholder="Place your search here"
				   bind:value={search}>
		</label>

		<datalist id="boys">
			{#each data as { name, tally }}
				<option value={name} on:click={(e) => {
					console.log(e)
				}}>{tally}</option>
			{/each}
		</datalist>
	</div>

	<div
		class="h-[calc(100%-110px)] bg-gray-900 rounded-2xl p-4 flex justify-center items-center">
		<CardBoy {selectedBoy} />
	</div>
</div>