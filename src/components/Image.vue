<template>
    <img :src="src">
</template>

<script>
    export default {
        name: 'Image',
        props: {
            src: {
                type: String,
                required: true,
            }
        }
    }
</script>

