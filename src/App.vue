<template>
  <div id="app" >
    <div class="row" >
      <div class="col-md-7" >
        <div class="row" >
          <div class="col-md-6" v-for="(p, key) in productos" :key="key" >
            <Producto 
            :agregado="estaEnCarrito(p)" 
            :producto="p" 
            @agregarP="agregarProducto" />
          </div>          
        </div>
      </div>
      <div class="col-md-5 my-5">
            <Carrito 
            :productos="carrito"
            @quitar="quitarProducto"/>
          </div>
    </div>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Producto from "./components/Producto.vue";
import productos from "./productos.json";
import Carrito from './components/Carrito.vue'

export default {
  name: "App",
  components: {
    Producto,
    Carrito
  },
  data(){
    return{
      productos,
      carrito:[],
    }
  },
  methods:{
    agregarProducto(p){
      this.carrito.push(p);
    },
    estaEnCarrito(p){
      const item = this.carrito.filter(i => i.id === p.id);
      
      if (item) {
        console.log(item);
        return true;
      }
      return false;
    }
    ,
    quitarProducto(p){
      this.carrito = this.carrito.filter(i => i.id != p.id);
    }
  }
};
</script>

<style>
</style>
