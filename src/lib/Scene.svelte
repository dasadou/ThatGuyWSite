<script lang="ts">
    import { T } from '@threlte/core'
    import { Grid, interactivity } from '@threlte/extras'
    import { spring } from 'svelte/motion'
    import Dice from "$lib/Dice.svelte";


    const { target } = interactivity()

    target.set(document.getElementById('int-target') ?? undefined)

    const pos = spring({ x: 0, z: 0 })
    const setRandomPos = () => {
        pos.set({
            x: Math.random() * 10 - 5,
            z: Math.random() * 10 - 5
        })
    }
</script>


<!--<T.AmbientLight intensity={0.4} />-->
<!--<T.DirectionalLight position={[1, 2, 5]} />-->

<Dice></Dice>

<!--<Grid-->
<!--        position.y={-0.001}-->
<!--        cellColor="red"-->
<!--        sectionColor="black"-->
<!--        sectionThickness={10}-->
<!--        fadeDistance={25}-->
<!--        cellSize={2}-->
<!--/>-->
