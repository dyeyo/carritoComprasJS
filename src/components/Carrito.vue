<template>
<div>
    <table id="lista-carrito" class="u-full-width">
        <thead>
            <tr>
                <th>Imagen</th>
                <th>Nombre</th>
                <th>Precio</th>
                <th></th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(item, index) in items" :key="index">
                <td>
                    <img :src="item.imagen" width="100">
                </td>
                <td>{{item.titulo}}</td>
                <td>${{item.precio}}</td>
                <td><button  @click="removerItem(item)" class="borrar-curso"> X</button></td>
            </tr>
        </tbody>
    </table>
    <div class="card my-5">
       <h4>Total : ${{total}}</h4>
    </div>
    <button :disabled="items.length === 0" class="btn btn-success float-right btn-block" @click="$emit('pagar')"> Pagar Ahora </button>
</div>
</template>
<script>
export default {
    name:'Carrito',
    props:['items'],
    computed:{
        total(){
            return this.items.reduce((acum, item)=> acum+ Number(item.precio),0)
        }
    },
    methods:{
        removerItem(item){
          this.$emit('eliminar-producto',item)
        }
    }
}
</script>