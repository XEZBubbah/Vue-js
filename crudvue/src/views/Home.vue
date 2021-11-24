<template>

<div class="container">

  <div class="texto"> 
    <h1>Ejercicio de Suma</h1>

    Nombre: <input type="text" v-model="nombre">

    <br>

    Bienvenido {{nombre}}

    <br>
    <hr>
    N1: <input type="text" v-model="n1">
    <br>
    N2: <input type="text" v-model="n2">
    <br>
    Total de la suma : {{suma}}
    <br>
    La multiplicación es : {{multipli}}
    <br>
    <button v-on:click="multiplicar">Multiplicar</button>
    <hr>
    <h1>Lista de productos</h1>
    <hr>
    <h3>Buscar</h3>
    <input type="text" v-model="txtBuscar">
  </div> 
  <table class="table">
    <thead>
      <tr>
        <th></th>
        <th></th>
        <th></th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td scope="row"></td>
        <td>Nombre</td>
        <td>Precio</td>
        <td>Cantidad</td>
        <td>Imagen</td>
      </tr>
      <tr v-for="producto in buscarProducto" :key="producto.nombre">
        <td scope="row"></td>
        <td>{{producto.nombre}}</td>
        <td>{{producto.precio}}</td>
        <td>{{producto.cantidad}}</td>
        <td> {{producto.img}} </td>
      </tr>
    </tbody>
  </table>

</div>

</template>

<script>
export default {
  
  data(){
    return{
      nombre: "",
      n1: "",
      n2: "",
      multipli: "",
      txtBuscar: "",

      productos: [
        {
          nombre: "MrBrown",
          precio: 2500,
          cantidad: 10,
          img: "https://www.merkadomi.com/wp-content/uploads/2020/09/bimbo-mr-brown-brownie-arequipe-1-1.jpg",
        },
        {
          nombre: "Leche Alquería",
          precio: 1500,
          cantidad: 35,
          img: "https://metrocolombiafood.vteximg.com.br/arquivos/ids/308281-1000-1000/7702177009208---ENTERA-1300-ADELANTE.jpg?v=637550533870230000",
        },
        {
          nombre: "M&M",
          precio: 1500,
          cantidad: 25,
          img: "https://jumbocolombiafood.vteximg.com.br/arquivos/ids/3724009-1000-1000/40000514510-1.jpg?v=637588485288800000",
        },
      ],
    }
  },

  methods:{

    multiplicar(){
      this.multipli = parseInt(this.n1) * parseInt(this.n2);
    }

  },

  computed: {

    buscarProducto(){

      return this.productos.filter(item => {
        return item.nombre.includes(this.txtBuscar);
      })

    },

    suma(){
      return parseInt(this.n1) + parseInt(this.n2);
    }

  }

}
</script>

<style scoped>

  .container{
    margin: 0 auto;
  }
  .texto{
    margin: 0 auto;
    text-align: center;
  }

</style>
