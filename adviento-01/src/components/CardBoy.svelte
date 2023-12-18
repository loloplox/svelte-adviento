<script>
	export let selectedBoy;
</script>

{#if selectedBoy.name !== ""}
	<div class="w-1/2">
		<h3 class="text-[200px]">
			{#if selectedBoy.tally < 0 && selectedBoy.name}
				👿
			{:else if selectedBoy.tally > 0}
				😇
			{:else}
				😐
			{/if}
		</h3>
	</div>
	<div class="w-1/2">
		<h3 class="text-xl">
			Name: {selectedBoy.name}
		</h3>
		<h3 class="text-xl">
			Tally: {selectedBoy.tally}
		</h3>
	</div>
{:else}
	<div class="w-full">
		<h3 class="text-center text-gray-400">
			Select a child in the table or search for one
		</h3>
	</div>
{/if}