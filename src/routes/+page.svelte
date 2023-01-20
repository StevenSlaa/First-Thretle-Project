<script lang="ts">
	import RackItem from '$lib/components/Diagrams/rackDiagram/RackItem.svelte';
	import { Canvas, OrbitControls, T} from '@threlte/core';
	import { spring } from 'svelte/motion';
	import { degToRad } from 'three/src/math/MathUtils';
	import Scene from '$lib/components/Diagrams/rackDiagram/Scene.svelte';
</script>

<div class="scene">
	<Canvas>
        <Scene/>
	</Canvas>
</div>
<!-- <div class="slidecontainer">
	<h3 class="title">Controls</h3>
	<div class="slider-input">
		<span>X</span>
		<input type="range" min="0" max="10" bind:value={val1} />
		<span>{val1 / 10}</span>
	</div>
	<div class="slider-input">
		<span>X</span>
		<input type="range" min="0" max="10" bind:value={val2} />
		<span>{val2 / 10}</span>
	</div>
	<div class="slider-input">
		<span>X</span>
		<input type="range" min="0" max="10" bind:value={val3} />
		<span>{val3 / 10}</span>
	</div>
</div> -->

<style lang="scss">
	.scene {
		height: 100%;
		width: 100%;
	}
	.slidecontainer {
		position: absolute;
		left: 50%;
		bottom: 12px;
		background: rgba(0, 0, 0, 0.5);
		backdrop-filter: blur(5px);
		color: white;
		transform: translateX(-50%);
		padding: 24px;
		text-align: center;
		border-radius: 24px;
		.title {
			margin-bottom: 12px;
		}
		.slider-input {
			display: flex;
			justify-content: flex-start;
			align-items: center;
			span {
				margin-right: 12px;
			}
		}
	}
</style>
