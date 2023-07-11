<template>
  <div class="about">
    <h1>This is add view</h1>
  </div>
  <div>
    <input v-model="newProduct.name" type="text" placeholder="Name">
    <input v-model="newProduct.price" type="number" placeholder="Price">
    <button @click="addProduct">Add</button>
  </div>
</template>


<script>
import axios from 'axios';

export default {
  data() {
    return {
      newProduct: {
        name: '',
        price: 0
      }
    };
  },
  methods: {
    addProduct() {
      axios.post('http://localhost:8000/book', this.newProduct)
        .then(response => {
          this.$emit('product-added', response.data);
          this.newProduct = {
            name: '',
            price: 0
          };
        })
        .catch(error => {
          console.error(error);
        });
    }
  }
};
</script>
