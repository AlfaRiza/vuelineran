<template>
  <div class="food-detail container">
    <Navbar />
    <h1>Food Detail</h1>

    <!-- breadcum -->
    <div class="row mt-5">
      <div class="col">
        <nav aria-label="breadcrumb">
          <ol class="breadcrumb">
            <router-link class="breadcrumb-item" to="/">Home</router-link>
            <router-link class="breadcrumb-item" to="/foods">Food</router-link>
            <li class="breadcrumb-item active" aria-current="page">
              Food Detail
            </li>
          </ol>
        </nav>
      </div>
    </div>

    <div class="row mt-3">
      <div class="col">
        <img
          :src="'../images/' + product.gambar"
          class="img-fluid shadow rounded"
          alt=""
        />
      </div>
      <div class="col">
        <h3>
          <strong>{{ product.nama }}</strong>
        </h3>
        <hr />
        <h4>
          Harga : <strong>Rp. {{ product.harga }}</strong>
        </h4>

        <form class="mt-4" v-on:submit.prevent>
          <div class="mb-3">
            <label for="jumlah" class="form-label">Jumlah</label>
            <input
              type="number"
              class="form-control"
              id="jumlah"
              placeholder="1"
              min="1"
              v-model="pesan.jumlah_pesanan"
            />
          </div>
          <div class="mb-3">
            <label for="keterangan" class="form-label">Keterangan</label>
            <textarea
              class="form-control"
              id="keterangan"
              rows="3"
              placeholder="eg. sambalnya banyakin"
              v-model="pesan.keterangan"
            ></textarea>
          </div>
          <button type="submit" @click="pemesanan" class="btn btn-success">
            <b-icon-cart></b-icon-cart> Pesan
          </button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import axios from "axios";
export default {
  name: "FoodDetail",
  components: {
    Navbar,
  },
  data() {
    return {
      product: [],
      pesan: {},
    };
  },
  methods: {
    setProduct(data) {
      this.product = data;
    },
    pemesanan() {
      if(this.pesan.jumlah_pesanan){
        this.$router.push({ path: '/keranjang' });
        this.pesan.products = this.product;
        axios
          .post("http://localhost:3000/keranjangs", this.pesan)
          .then(() => {
            this.$toast.success("Berhasil masuk ke keranjang", {
              type: 'success',
              position: 'top-right',
              duration: 3000,
              dismissible: true
            });
          })
          .catch((err) => console.log(err));
      }else{
        this.$toast.error("Jumlah makanan harus diisi", {
              type: 'error',
              position: 'top-right',
              duration: 3000,
              dismissible: true
            });
      }
    },
  },
  mounted() {
    axios
      .get("http://localhost:3000/products/" + this.$route.params.id)
      .then((response) => {
        // handle success
        this.setProduct(response.data);
        // console.log(response);
      })
      .catch((error) => {
        // handle error
        console.log("Gagal : ", error);
      });
  },
};
</script>

<style scoped>
</style>