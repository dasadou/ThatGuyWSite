<script lang="ts">
    import {Canvas} from '@threlte/core'
    import Dice from "$lib/Dice.svelte";
    import Scene from "$lib/Scene.svelte";
    import {World} from "@threlte/rapier";
</script>

<h1>Bienvenue dans ma page web</h1>
<!-- <p>Visit <a href="https://svelte.dev/docs/kit">svelte.dev/docs/kit</a> to read the documentation</p> -->
<Canvas>
    <World>

        <Scene/>
    </World>
</Canvas>
