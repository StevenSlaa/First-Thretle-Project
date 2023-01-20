<script lang="ts">
	import RackItem from '$lib/components/Diagrams/rackDiagram/RackItem.svelte';
	import { OrbitControls, T} from '@threlte/core';
	import { degToRad } from 'three/src/math/MathUtils';
    export let singleUnitSize: number = 1/4;

	let rackItems: number[] = [1,3,1,2];
    function getNextPosition(nextIndex: number){
        let positionY = 0;
        for(let i = 0; i < nextIndex + 1; i++){
            const itemSize = rackItems[i] * singleUnitSize;
            if (i === 0){
                positionY = itemSize / 2;
            }else{
                const previousItemSize = rackItems[i-1] * singleUnitSize;
                positionY += itemSize / 2 + previousItemSize/2 
            }
            
        }
        return positionY;
    }
    function generateRandomColor(){
        let r = Math.round(Math.random() * 255).toString(16);
        let g = Math.round(Math.random() * 255).toString(16);
        let b = Math.round(Math.random() * 255).toString(16);
        let color = String(Math.random() * 0xffffff)
        if (r.length == 1)
            r = "0" + r;
        if (g.length == 1)
            g = "0" + g;
        if (b.length == 1)
            b = "0" + b;
        return "#" + r + g + b;
    }
    console.log(generateRandomColor())
</script>


<T.PerspectiveCamera makeDefault position={[10, 10, 10]} fov={24}>
    <OrbitControls maxPolarAngle={degToRad(80)} enableZoom={true} target={{ y: 0.5 }} />
</T.PerspectiveCamera>

<T.DirectionalLight castShadow position={[3, 10, 10]} />
<T.DirectionalLight position={[-3, 10, -10]} intensity={0.2} />
<T.AmbientLight intensity={0.2} />

<!-- Cube -->
{#each rackItems as item, i}
    <RackItem itemId={String(i)}
    scale={[1,singleUnitSize* item, 1]} 
    positionY={getNextPosition(i)} 
    color={generateRandomColor()}/>
{/each}

<!-- Floor -->
<T.Mesh receiveShadow rotation.x={degToRad(-90)}>
    <T.CircleGeometry args={[3, 72]} />
    <T.MeshStandardMaterial color="white" opacity={.5} transparent/>
</T.Mesh>