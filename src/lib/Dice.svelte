<script lang="ts">
    import {useTask} from '@threlte/core';
    import {RigidBody} from "@threlte/rapier";
    import {HTML, interactivity, RoundedBoxGeometry} from "@threlte/extras";
    import {CanvasTexture, Euler, MeshBasicMaterial} from "three";

    // let speed: Vector3 = new Vector3(2, 2, 2);
    // let cube: any;
    let faces: any;
    let roundedBoxDimension = [1.5, 1.5, 1.5] as unknown as undefined;
    // const {start, stop, started, task} = useTask(
    const {start, stop} = useTask(
        (delta) => {
            // This function will be executed on every frame
            let randomRot = getRandomRotation();

            faces.rotation.set(randomRot.x, randomRot.y, randomRot.z / 10, "XYZ");
            // cube.applyTorqueImpulse(new Vector3(0, 1, 0));
        }, {autoStart: false}
    )
    // TODO: make a smooth transition to show face directly to camera by slowing down rotation

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
        return new Euler(Math.random() * 10, Math.random() * 10, Math.random() * 10)

    }
</script>

<!-- face.materialIndex = face du de --
linearVelocity={[5,5,5]}
-->
<RigidBody>

    <T.Mesh position.y={0.15}
            material={materials}

            oncreate={(e)=>{ faces = e.valueOf(); console.log(faces);}}
            onpointerup={()=>{
            console.log("should start")
            stop();
        }}

            onpointerdown={()=>{
            console.log("should stop");
            start();
            // cube.object.rotation.set(randomRot.x,randomRot.y,randomRot.z,"XYZ");
        }}


            onclick={(e) => {
    console.log(e.intersections[0].face.materialIndex + 1);
  }}>


        <RoundedBoxGeometry args={roundedBoxDimension}/>
    </T.Mesh>

    <HTML position={[1,1,1]}>

    <div>WHATATATATATAT</div>
    </HTML>
</RigidBody>
