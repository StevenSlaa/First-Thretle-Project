<script>
    import RackItem from '$lib/components/Diagrams/rackDiagram/RackItem.svelte';
import { Canvas, InteractiveObject, OrbitControls, T } from '@threlte/core'
    import { spring } from 'svelte/motion'
    import { degToRad } from 'three/src/math/MathUtils'
    let val1 = 1
    let val2 = 1
    let val3 = 1
    $: scale = [val1, val2, val3]


    let rackItems = [1,2,2,1,1,2,1,1]
</script>

<div class="scene">
    <Canvas>
        <T.PerspectiveCamera makeDefault position={[10, 10, 10]} fov={24}>
            <OrbitControls maxPolarAngle={degToRad(80)} enableZoom={false} target={{ y: 0.5 }} />
        </T.PerspectiveCamera>

        <T.DirectionalLight castShadow position={[3, 10, 10]} />
        <T.DirectionalLight position={[-3, 10, -10]} intensity={0.2} />
        <T.AmbientLight intensity={0.2} />

        <!-- Cube -->
        <RackItem scale={scale}/>
        <!-- {#each rackItems as item}
            
        {/each} -->

        <!-- Floor -->
        <T.Mesh receiveShadow rotation.x={degToRad(-90)}>
            <T.CircleGeometry args={[3, 72]} />
            <T.MeshStandardMaterial color="white" />
        </T.Mesh>
    </Canvas>
</div>
<div class="slidecontainer">
    <h3 class="title">Controls</h3>
    <div class="slider-input">
        <span>X</span>
        <input type="range" min="0" max="10" bind:value={val1}>
        <span>{val1}</span>
    </div>
    <div class="slider-input">
        <span>X</span>
        <input type="range" min="0" max="10" bind:value={val2}>
        <span>{val2}</span>
    </div>
    <div class="slider-input">
        <span>X</span>
        <input type="range" min="0" max="10" bind:value={val3}>
        <span>{val3}</span>
    </div>
    
</div>

<style lang="scss">
    .scene {
        height: 100%;
        width: 100%;
    }
    .slidecontainer{
        position: absolute;
        left: 50%;
        bottom: 12px;
        background: rgba(0,0,0,.5);
        backdrop-filter: blur(5px);
        color: white;
        transform: translateX(-50%);
        padding: 24px;
        text-align: center;
        border-radius: 24px;
        .title{
            margin-bottom: 12px;
        }
        .slider-input{
            display: flex;
            justify-content: flex-start;
            align-items: center;
            span{margin-right: 12px;}
        }
    }
</style>