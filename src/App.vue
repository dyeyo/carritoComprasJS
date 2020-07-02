<template>
  <div id="app">
    <header id="header" class="header">
    <div class="container">
        <div class="row">
            <div class="col-md-8">
                <img src="img/logo.jpg" id="logo">
            </div>
            <div class="col-md-4">
                <ul>
                  <li class="submenu">
                    <img src="img/cart.png" id="img-carrito">
                    <div id="carrito">
                        <Carrito :items="carrito" v-on:eliminar-producto="removerItemCarrito" v-on:pagar="finalizarPago"></Carrito>
                        <a @click="vaciarCarro()" id="vaciar-carrito" class="button u-full-width">Vaciar Carrito</a>
                    </div>
                  </li>
                </ul>
            </div>
        </div> 
    </div>
    </header>
    <div id="hero">
        <div class="container">
            <div class="row">
                    <div class="six columns">
                        <div class="contenido-hero">
                                <h2>Aprende algo nuevo</h2>
                                <p>Todos los cursos a $15</p>
                                <form action="#" id="busqueda" method="post" class="formulario clase2 clase3">
                                    <input class="u-full-width" type="text" placeholder="¿Que te gustaría Aprender?" id="buscador">
                                    <input type="submit" id="submit-buscador" class="submit-buscador">
                                </form>
                        </div>
                    </div>
            </div> 
        </div>
    </div>
    <div id="lista-cursos" class="container">
        <h1 id="encabezado" class="encabezado">Cursos En Línea</h1>
        <div class="row">
           <div class="col-md-4" v-for="prod in productos" :key="prod.id">
            <Productos :producto="prod" v-on:agregar-carro="agregarProdCarro" :estaEnCarrito="productoExisteCarrito(prod)"></Productos>
          </div>
        </div> 
    </div>  
  </div>
</template>

<script>

import Productos from './components/Productos'
import Carrito from './components/Carrito'
import productos from './productos.json'
export default {
  name: 'App',
  data(){
    return{
      productos,
      carrito:[]
    }
  },
  components: {
    Productos,
    Carrito
  },
  methods:{
    agregarProdCarro(producto){
      this.carrito.push(producto)
    },
    productoExisteCarrito(producto){
      const item = this.carrito.find(item => item.id === producto.id)
      if (item) {
        return true
      }else{
        return false
      }
    },
    removerItemCarrito(producto){
      this.carrito = this.carrito.filter(item => item.id != producto.id)
    },
    finalizarPago(){
      this.carrito=[]
      alert('Venta Completada')
    },
    vaciarCarro(){
      this.carrito=[]
    }
  }
}
</script>

<style>
</style>
