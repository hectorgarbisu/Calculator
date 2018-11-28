<template>
    <footer class="card-footer">
        <div v-if="isLoadingSwag" class="card-footer-item">
            <the-loader/> 
            <p class="padding-left-20"> {{ currentMessage }} </p>
        </div>
        <div v-else class="card-footer-item"> 
            <p> Puntuación final: <span class="has-text-info">{{ score }}</span> swags</p>
        </div>
    </footer>    

</template>



<script>
import TheLoader from './loader.vue'

export default {

    data() {
        return {
            messages: [ "Consultado bases de datos mundiales de swag",
                        "Haciendo análisis de características complejas",
                        "Implementando modelos de deep learning",
                        "Intendando eliminar sexismo en el modelo de regresión",
                        "Intento de extracción fallido, arreglando resultados",
                        "Pausa dramática" ],
            currentMessageIndex: 0,
            isLoadingSwag:  false,
            
        }
    },

    computed: {

        currentMessage() {
            return this.messages[this.currentMessageIndex]
        },
    },

    components: { TheLoader },

    props: [ 'score' ],

    mounted() {

        this.startTimeOut()

    },

    methods: {

        startTimeOut(){
            // sets the spinner
            this.isLoadingSwag = true 

            var interval = setInterval(() => {
                // rolls every message at a fixed interval until the  last one is reached
                this.currentMessageIndex++
                if ( this.currentMessageIndex >= this.messages.length ) {
                  clearInterval(interval)
                  this.isLoadingSwag = false
                }

            }, 2000);

        },


    }

}


</script>




<style>
    .padding-left-20 {
        padding-left: 20px;
    }
</style>




