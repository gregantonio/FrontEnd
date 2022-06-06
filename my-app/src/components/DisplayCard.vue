<template>
    <div class="display-board">
        <h4>Most Recent Flight 1</h4>
        <div class="number">
        {{numberOfUsers}}
        </div>
        <div class="btn">
            <button @click='getAllUsers()' type="button" class="btn btn-warning">blank</button>
        </div>        
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