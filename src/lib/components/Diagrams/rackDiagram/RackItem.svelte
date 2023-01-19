<script>
    import { InteractiveObject, T } from '@threlte/core'
    import { spring } from 'svelte/motion'

    export let scale = [1,1,1];
</script>

<T.Group>
    <T.Mesh position.y={scale[1]/2} castShadow let:ref>
        <!-- Add interaction -->
        <InteractiveObject object={ref} interactive/>
        <T.BoxGeometry args={scale} />
        <T.MeshStandardMaterial color="#333333" />
    </T.Mesh>
</T.Group>