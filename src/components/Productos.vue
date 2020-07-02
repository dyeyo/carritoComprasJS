<template>
    <div class="">
        <div class="card mt-5">
            <img :src="producto.imagen" class="imagen-curso u-full-width">
            <div class="info-card">
                <h4>{{producto.titulo}}</h4>
                <p>Juan Pedro</p>
                <img src="img/estrellas.png">
                <p class="precio">$10000 <span class="u-pull-right ">$ {{ Number(producto.precio).toFixed()}}</span></p>
                <button class="btn btn-primary btn-block" @click="agregarCarrito(producto)" :disabled="estaEnCarrito">{{estaEnCarrito ? 'Producto Agregado' : 'Agregar al Carrito'}}</button>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name:'Productos',
    props:['producto','estaEnCarrito'],
    methods:{
        agregarCarrito(producto){
            this.$emit('agregar-carro',producto)
        }
    }
}
</script>