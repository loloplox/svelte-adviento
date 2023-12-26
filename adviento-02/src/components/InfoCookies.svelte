<script>
    export let eatenCookies, restartCookie, removeCookie, addCookie
</script>

<div class="flex gap-4">
    <div class="bg-gray-900 rounded-2xl p-4">
        <p class="text-center text-2xl text-white">Galletas comidas: {eatenCookies}</p>
    </div>

    <button class="bg-yellow-500 rounded-2xl p-4 text-center text-2xl text-white" on:click={removeCookie}>
        -1
    </button>

    <button class="bg-red-500 rounded-2xl p-4 text-center text-2xl text-white" on:click={restartCookie}>
        Reset
    </button>
</div>