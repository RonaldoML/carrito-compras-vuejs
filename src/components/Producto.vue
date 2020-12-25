<template>
    <div class="card my-5">
        <div class="card-body">
            <h5 class="card-title text-center">
                {{ producto.titulo }}
            </h5>
            <img :src="producto.imagen" class="card-img-top">
            <p class="card-text">${{ producto.precio }}</p>
            <button class="btn btn-primary form-control" 
                @click="agregar" 
                :disabled="agregado">
                {{agregado ? 'Agregado' :'Agregar al carrito'}}
            </button>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Producto',
        props:{
            producto: {
                type: Object
            },
            agregado: {
                type: Boolean,
            }
        },
        methods:{
            agregar(){
                this.$emit('agregarP', this.producto);
            }
        }
    }
</script>

<style scoped>

</style>