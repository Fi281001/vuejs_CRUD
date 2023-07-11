<script >
import Add from '../views/addview.vue';
import axios from 'axios'
export default {
  components: {
    Add
  },
  name: 'ProductList',
  data() {
    return {
      products: [],
    }
  },
  created() {
    this.getProducts()
  },
  methods: {
    
    getProducts() {
    

      axios.get(`http://localhost:8000/book`)
        .then(response => {
          this.products = response.data;
          console.log(this.products);
          
        })
        .catch(error => {
          console.error(error);
        });
    },
    //theem san pham de hien thi danh sach
    // productAdded(newProduct) {
    //   this.products.push(newProduct);
    // },
    deleteProduct(product) {
    axios.delete(`http://localhost:8000/book/${product.id}`).then(response => {
        // Xóa sản phẩm khoi danh sách
        const index = this.products.findIndex(p => p.id === product.id);
        if (index !== -1) {
          this.products.splice(index, 1);
        }
      })
      .catch(error => {
        console.error(error);
      });
  }

  }
}
</script>

<template>
 
    <table class="table">
    <thead>
      <tr>
        <th>Name</th>
        <th>Price</th>
        <th>action</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="product in products" :key="product.id">
        <td>{{ product.name }}</td>
        <td>{{ product.price }}</td>
        <td>
          <button @click="editProduct(product)">Edit</button>
          <button @click="deleteProduct(product)">Delete</button>
        </td>
      </tr>
    </tbody>
  </table>
</template>
