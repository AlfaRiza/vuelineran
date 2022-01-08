<template>
<div class="container">
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">Vuenileran</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav">
                <li class="nav-item">
                    <router-link class="nav-link" to="/">Home</router-link>
                </li>
                <li class="nav-item">
                    <router-link class="nav-link" to="/foods">Foods</router-link>
                </li>
            </ul>
            <ul class="navbar-nav ml-auto">
                <li class="nav-item">
                    <router-link class="nav-link" to="/keranjang">
                    Keranjang 
                    <b-icon-cart></b-icon-cart>
                    <span class="badge badge-success ml-2">{{ updateKeranjang ? updateKeranjang.length : jumlah_pesanans.length }}</span>
                    </router-link>
                </li>
            </ul>
            </div>
        </div>
        </nav>
    </div>
</template>

<script>
import axios from "axios";
export default {
    name: 'Navbar',
    data() {
        return {
            jumlah_pesanans: [],
        }
    },
    props: ['updateKeranjang'],
    methods: {
        setJumlah(data){
            this.jumlah_pesanans = data
        }
    },
    mounted() {
        axios.get('http://localhost:3000/keranjangs')
        .then( (response) => {
        // handle success
        this.setJumlah(response.data)
        })
        .catch( (error) => {
        // handle error
        console.log("Gagal : ",error);
        })
    },
}
</script>

<style>

</style>