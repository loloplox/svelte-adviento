<script>

	import Table from '../components/Table.svelte';
	import axios from 'axios';
	import Searcher from '../components/Searcher.svelte';

	let data = [];
	let selectedBoy = {
		name: '',
		tally: 0
	};
	let search = '';


	async function getData() {
		const response = await axios.get('https://advent.sveltesociety.dev/data/2023/day-one.json');

		data = response.data;
	}

	function handleClick(tableSelected) {
		selectedBoy = tableSelected;
		search = selectedBoy.name;
	}

	getData();

</script>

<div class="h-full p-4">
	<h1 class="text-center text-5xl font-bold mb-4 title">
		Bueno o Travieso
	</h1>

	<div class="grid grid-cols-2 gap-4">
		<div class="h-[600px] bg-gray-800 rounded px-6 py-4">
			<Searcher {data} {selectedBoy} {search} />
		</div>

		<div class="h-[600px] bg-gray-800 rounded overflow-hidden px-6 py-4">
			<Table {data} {handleClick} />
		</div>
	</div>
</div>

<style>
    .title {
        background: #4dff70; /* fallback for old browsers */
        background: -webkit-linear-gradient(to right, #4dff70, #ff4d4d); /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(to right, #4dff70, #ff4d4d); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
        -webkit-background-clip: text;
        background-clip: text;
        color: transparent;
    }
</style>