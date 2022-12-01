<template>
  <div id="app">
    <ul>
      <li>Lista productos</li>
      <li v-for="(producto, index) in productos" :key="index">
        {{ producto.nombre }} - {{ producto.precio }}
      </li>
      <li>Total a pagar {{ totalPagar }}</li>
    </ul>
    <div v-if="ganaDescuento">GANASTE DESCUENTO!!!</div>
    <label for="">Nombre </label>
    <input type="text" v-model="nuevoProducto" /><br />
    <label for="">Precio </label>
    <input type="text" v-model="nuevoPrecio" /><br />

    <button @click="addProducto">Añadir producto</button>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},

  data: function () {
    return {
      nuevoProducto: "",
      nuevoPrecio: "",
      productos: [],
      totalPagar: 0,
      // muchasProductos: false,
    };
  },

  methods: {
    addProducto() {
      this.productos.push({
        nombre: this.nuevoProducto,
        precio: this.nuevoPrecio,
      });

      this.totalPagar += parseInt(this.nuevoPrecio);

      this.nuevoProducto = "";
      this.nuevoPrecio = "";
    },
  },

  computed: {
    ganaDescuento() {
      // Operador ternario - Elvis Operator
      //return this.productos.length > 5 ? true : false;

      if (this.totalPagar > 100) {
        return true;
      } else {
        return false;
      }
    },
  },
};
</script>

<style>
ul {
  width: 420px;
  margin: 0 auto;
  background: gainsboro;
  border-radius: 8px;
}
</style>
