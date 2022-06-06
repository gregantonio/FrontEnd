<template>
    <div class="display-board"> 
    </div>
</template>

<script>
    export default {
        name: 'DisplayCard',
        props: ['numberOfUsers'],
        methods: {
            getAllUsers() {
                this.$emit('getAllUsers')
            }
        }
    }
</script>