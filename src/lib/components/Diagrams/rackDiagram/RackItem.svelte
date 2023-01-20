<script lang="ts">
    import { InteractiveObject, T } from '@threlte/core'
    import { spring } from 'svelte/motion'
    import { Editable } from '@threlte/theatre'
    export let scale = [1,1,1];
    export let positionY: number = 2;
    export let color: string = "#333333"
    export let itemId: string = "test"
</script>

<T.Group position.y={positionY}>
    
    <T.Mesh castShadow let:ref>
        <!-- Add interaction -->
        <InteractiveObject object={ref} interactive/>
        <T.BoxGeometry args={scale} />
        <T.MeshStandardMaterial color={color} />
    </T.Mesh>
</T.Group>