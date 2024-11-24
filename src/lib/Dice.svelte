<script lang="ts">
    import {T} from '@threlte/core';
    import {OrbitControls} from "@threlte/extras";
    import {BoxGeometry, CanvasTexture, MeshBasicMaterial} from "three";

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
</script>

<!-- face.materialIndex = face du de
 ou bien -->
<T.Mesh position.y={0} material={materials} onclick={(ref:any) => {
    console.log(ref.intersections[0].face.materialIndex + 1);
  }}>
    <T.BoxGeometry args={[10, 10, 10]}/>
</T.Mesh>

<T.PerspectiveCamera
        makeDefault
        position={[10, 10, 10]}
        oncreate={(ref) => {
    ref.lookAt(0, 0, 0);
  }}
>
    <OrbitControls !autoRotate></OrbitControls>
</T.PerspectiveCamera>

