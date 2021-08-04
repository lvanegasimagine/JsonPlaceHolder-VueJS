<template>
   <Titulo texto="Ruta con Parametros"/>
   <h1>Parametro: {{$route.params.id}}</h1>
   <h3>Titulo</h3>
   <!-- <br> -->
   <h3>{{articulo.title}}</h3>
   <p>Descripción</p>
   <p>{{articulo.body}}</p>
</template>

<script>
import Titulo from '../components/Titulo.vue'

export default {
    components: {
        Titulo
    },
    data() {
        return {
            articulo: {}
        }
    },
    methods: {
        async consumirArticulo() {
            try {
                const data = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
                const objeto = await data.json();
                this.articulo = objeto;
                console.log(this.articulo)
            } catch (error) {
                
            }
        }
    },
    created () {
        this.consumirArticulo();
    },
}
</script>

<style>

</style>