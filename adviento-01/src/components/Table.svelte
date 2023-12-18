<script>
	const SORT_TYPE = {
		ASC: 'asc',
		DESC: 'desc'
	};

	export let data;
	export let handleClick;

	let sortByName = {
		active: false,
		type: SORT_TYPE.ASC,
		change: () => {
			sortByName.active = true;
			sortByName.type = sortByName.type === SORT_TYPE.ASC ? SORT_TYPE.DESC : SORT_TYPE.ASC;
			sortByTally.active = false;

			data = data.sort((a, b) => {
				if (sortByName.type === SORT_TYPE.ASC) {
					return a.name.localeCompare(b.name);
				} else {
					return b.name.localeCompare(a.name);
				}
			});
		}
	};
	let sortByTally = {
		active: false,
		type: SORT_TYPE.ASC,
		change: () => {
			sortByTally.active = true;
			sortByTally.type = sortByTally.type === SORT_TYPE.ASC ? SORT_TYPE.DESC : SORT_TYPE.ASC;
			sortByName.active = false;

			data = data.sort((a, b) => {
				if (sortByTally.type === SORT_TYPE.ASC) {
					return a.tally - b.tally;
				} else {
					return b.tally - a.tally;
				}
			});

		}
	};


</script>


<div
	class="w-full h-full flex flex-col gap-4">

	<div>
		<table
			class="table-fixed w-full overflow-hidden rounded-2xl text-center">
			<thead class="bg-gray-900">
				<tr>
					<td
						class="p-3 font-bold cursor-pointer"
						on:click={sortByName.change}
					>
						<div class="flex justify-center items-center gap-2">
							Name
							<div class="w-5 h-5">
								{#if sortByName.active}
									{#if sortByName.type === SORT_TYPE.ASC}
										👇
									{:else if sortByName.type === SORT_TYPE.DESC}
										👆
									{/if}
								{:else}
									🤔
								{/if}
							</div>
						</div>
					</td>
					<td
						class="p-3 font-bold cursor-pointer"
						on:click={sortByTally.change}
					>
						<div class="flex justify-center items-center gap-2">
							Tally
							<div class="w-5 h-5">
								{#if sortByTally.active}
									{#if sortByTally.type === SORT_TYPE.ASC}
										🪨
									{:else if sortByTally.type === SORT_TYPE.DESC}
										🎁
									{/if}
								{:else}
									🤔
								{/if}
							</div>
						</div>
					</td>
				</tr>
			</thead>
		</table>
	</div>


	<div
		class=" overflow-y-scroll rounded-l-2xl scrollbar-thin scrollbar-thumb-gray-700">
		<table class="table-fixed text-center w-full">
			<tbody class="bg-gray-900 cursor-pointer">
				{#each data as { name, tally }}
					<tr class="hover:bg-gray-700"
						on:click={() => handleClick({name, tally})}>
						<td class="p-2">{name}</td>
						<td
							class="p-2 {tally > 0 ? 'text-green-400' : 'text-red-400'}">{tally}</td>
					</tr>
				{/each}
		</table>
	</div>
</div>