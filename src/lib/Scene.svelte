<script lang="ts">
    import {T} from '@threlte/core'
    import {Grid, interactivity, TrackballControls} from '@threlte/extras'
    import {spring} from 'svelte/motion'
    import Dice from "$lib/Dice.svelte";


</script>


<T.GridHelper args={[5, 5]}/>
<T.PerspectiveCamera
        makeDefault
        position={[1, 1, 1]}
        oncreate={(ref) => {
    ref.lookAt(0, 0, 0);
  }}
>
    <TrackballControls rotateSpeed=10></TrackballControls>
</T.PerspectiveCamera>


<Dice></Dice>
