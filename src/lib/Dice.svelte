<script lang="ts">
    import {T, useThrelte} from '@threlte/core';
    import {interactivity, TrackballControls} from "@threlte/extras";
    import {BoxGeometry, CanvasTexture, MeshBasicMaterial} from "three";
    import {get} from "svelte/store";

    export let rotateSpeed: number = 10;
    interactivity();

    function createTextTexture(text: string) {
        const canvas = document.createElement('canvas');
        const context = canvas.getContext('2d');
        if (!context) return;
        canvas.width = 256;
        canvas.height = 256;
        context.fillStyle = 'white';
        context.fillRect(0, 0, canvas.width, canvas.height);
        context.fillStyle = 'black';
        context.font = '40px Arial';

        const textMetrics = context.measureText(text);
        const textWidth = textMetrics.width;
        const x = (canvas.width - textWidth) / 2;
        const y = canvas.height / 2 + 20;

        context.fillText(text, x, y);
        return new CanvasTexture(canvas);
    }

    // Text for each face of the cube
    const textArray = ['1', '2', '3', '4', '5', '6'];
    const textures = textArray.map(text => createTextTexture(text));

    // Create the materials for the cube
    const materials = textures.map(texture => new MeshBasicMaterial({map: texture}));

    function getRandomRotation() {
        // Generate random rotation angles 
        const x = Math.random() * 2 * Math.PI;
        const y = Math.random() * 2 * Math.PI;
        const z = Math.random() * 2 * Math.PI;
        return {x, y, z};
    }

    let cube: any;
    const {scene, invalidate} = useThrelte();

    function onDiceClick() {
        // console.log('camera');
        // console.log(camera);
        // camera.lookAt(0, 0, 0);
        // if(cube){
        console.log('onDiceClick1');
        console.log(cube);
        console.log(typeof cube);
        const randomRotation = getRandomRotation();
        console.log('randomRotation', randomRotation);
        console.log("rotation: ", cube.rotation);
        cube.rotation.set(randomRotation.x, randomRotation.y, randomRotation.z);
        // }

    }

</script>
<T.GridHelper args={[10, 10]}/>

<!-- face.materialIndex = face du de -->
<T.Mesh
        onpointerover={(e)=>{
            const randomRot = getRandomRotation();
            e.object.rotation.set(randomRot.x,randomRot.y,randomRot.z,"XYZ");
        }}
        position.y={0.5}
        material={materials}
        onclick={(ref:any) => {
    console.log(ref.intersections[0].face.materialIndex + 1);
    onDiceClick();
  }}>
    <T.BoxGeometry args={[1, 1, 1]}/>
</T.Mesh>

<T.PerspectiveCamera
        bind:this={camera}
        makeDefault
        position={[1, 1, 1]}
        oncreate={(ref) => {
    ref.lookAt(0, 0, 0);
  }}
>
    <TrackballControls {rotateSpeed}></TrackballControls>
</T.PerspectiveCamera>

