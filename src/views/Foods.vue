<template>
  <div class="foods">
    <Navbar />
    <div class="container">
      <div class="row">
        <div class="col">
          <h2>Daftar <strong>Makanan</strong></h2>
        </div>
      </div>

      <div class="row d-flex justify-content-center">
        <div class="col-md-6">
          <div class="input-group mb-3">
            <input
              v-model="search"
              type="text"
              class="form-control"
              placeholder="Recipient's username"
              aria-label="Recipient's username"
              aria-describedby="basic-addon2"
              @keyup="searchProduct"
            />
            <span class="input-group-text" id="basic-addon2"
              ><b-icon-search></b-icon-search
            ></span>
          </div>
        </div>
      </div>

      <div class="row mb-4">
        <div
          class="col-md-3 mt-4"
          v-for="product in products"
          :key="product.id"
        >
          <CardProduct :product="product" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import CardProduct from "@/components/CardProduct.vue";
import axios from "axios";
export default {
  name: "Foods",
  components: {
    Navbar,
    CardProduct,
  },
  data() {
    return {
      products: [],
      search: "",
    };
  },
  methods: {
    setProduct(data) {
      this.products = data;
    },
    searchProduct() {
      axios
        .get("http://localhost:3000/products?q="+this.search)
        .then((response) => {
          // handle success
          this.setProduct(response.data);
        })
        .catch((error) => {
          // handle error
          console.log("Gagal : ", error);
        });
    },
  },
  mounted() {
    axios
      .get("http://localhost:3000/products")
      .then((response) => {
        // handle success
        this.setProduct(response.data);
      })
      .catch((error) => {
        // handle error
        console.log("Gagal : ", error);
      });
  },
};
</script>

<style>
</style>