<template>
    <div>
        hola {{ score }}
    </div>    
</template>



<script>
export default {

    data() {
        return {
            


        }
    },

    props: ['score'],

    mounted() {
        /** First time the requirements for this to display are met */
        /** Beauitful, intrusive, over the top loading animation goes here  */

        console.log("mounted")
    },

}


</script>




<style>
    
</style>




