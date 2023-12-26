<script>
    import Cookie from "../components/Cookie.svelte"

    let eatenCookies = 0

    function restartCookie() {
        eatenCookies = 0
    }

    function addCookie() {
        eatenCookies++
    }

    function removeCookie() {
        if (eatenCookies > 0) {
            eatenCookies--
        }
    }

</script>

<div class="grid grid-cols-1 place-items-center p-4">
    <h1 class="text-white text-4xl uppercase font-bold">Contador de galletas 🍪🎅</h1>

    <Cookie {eatenCookies} {restartCookie} {addCookie} {removeCookie}/>
</div>