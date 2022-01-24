<template>
    <div>
        Task: {{this.newTaskArray}}
    </div>
</template>

<script>
    export default {
        name: "list",
        props: {
            newTaskArray: {
                type: Array,
                default() {
                    return {}
                } 
            },
        },
        data() {
            return {
                
            }
        },
        methods: {
        }
    }
</script>

<style lang="css" >

</style>