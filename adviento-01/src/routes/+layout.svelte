<script>
	import '../app.css';
</script>

<main class="h-screen text-white">
	<slot />
</main>

<style lang="postcss">
    :global(html) {
        background-color: theme(colors.gray.900);
    }
</style>
