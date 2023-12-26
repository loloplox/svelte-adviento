<script>
    import { tweened } from 'svelte/motion'
    import { elasticOut } from 'svelte/easing'
    import InfoCookies from "./InfoCookies.svelte"

    export let eatenCookies, restartCookie, addCookie, removeCookie

    const durationMotion = 200


    let sizeCookie = tweened(1, {
        duration: durationMotion,
        easing: elasticOut
    })

    let cookiePhase = 1
    $: cookieUri = `/cookie_${ cookiePhase }.svg`

    function changePhase() {
        if (cookiePhase === 4) {
            addCookie()
            cookiePhase = 0
        }

        popAnimation(sizeCookie)

        cookiePhase++
    }

    function popAnimation(value) {
        value.set(1.02)

        setTimeout(() => {
            value.set(0.98)
        }, durationMotion / 2)

        setTimeout(() => {
            value.set(1)
        }, durationMotion)
    }

</script>

<button on:click={changePhase} class="w-[500px] h-[500px] mt-10">
    <picture>
        <img src={cookieUri} alt="Cookie" class="object-cover w-full" style="transform: scale({$sizeCookie});">
    </picture>
</button>

<InfoCookies {eatenCookies} {restartCookie} {addCookie} {removeCookie} />