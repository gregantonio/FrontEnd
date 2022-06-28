<template>
    <div class="display-board">
        <h4>Most Popular Airline</h4>
        <div class="number">
        {{numberOfUsers}}
        </div>
        <div class="btn">
            <FTButton @click='getAllUsers()' type="button" class="btn btn-warning">blank</FTButton>
        </div>        
    </div>
</template>

<script>
    export default {
        name: 'DisplayBoard',
        props: ['numberOfUsers'],
        methods: {
            getAllUsers() {
                this.$emit('getAllUsers')
            }
        }
    }
</script>