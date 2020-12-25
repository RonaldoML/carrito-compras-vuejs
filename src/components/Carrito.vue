<template>
    <div>
        <ul class="list-group">
            <li 
                v-for="(p, key) in productos"
                :key="key"
                class="list-group-item" 
                @click="quitar(p)">
                {{ p.titulo }} - ${{ p.precio }}
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: 'Carrito',
        props:{
            productos:{
                type: Array
            },
        },
        methods: {
            quitar(p){
                this.$emit('quitar', p)
            }
        },
    }
</script>

<style scoped>

</style>