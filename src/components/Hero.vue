<template>
  <div class="hero">
    <div class="container">
      <!-- Desktop -->
      <div class="d-none d-md-block">
        <div class="row mt-5">
          <div class="col-6 d-flex">
            <div class="justify-content-center align-self-center">
              <h2>
                <strong class="text-success">Delicious</strong> Food Menu
                <br />
                In your <strong class="text-success">Gadged</strong>
              </h2>
              <p class="mt-2">Ayo, segera pesan makanan favorit antum</p>
              <router-link to="/foods" class="btn btn-lg btn-success mt-3">
                <b-icon-arrow-right> </b-icon-arrow-right> Pesan</router-link
              >
            </div>
          </div>
          <div class="col-6">
            <img width="100%" src="../assets/images/hero.png" alt="" />
          </div>
        </div>
      </div>

      <!-- Mobile -->
      <div class="d-md-none d-sm-block">
        <div class="row mt-5">
          <div class="col-12">
            <img width="100%" src="../assets/images/hero.png" alt="" />
          </div>
          <div class="col-12 d-flex mt-3">
            <div class="justify-content-center align-self-center">
              <h2>
                <strong class="text-success">Delicious</strong> Food Menu
                <br />
                In your <strong class="text-success">Gadged</strong>
              </h2>
              <p class="mt-2">Ayo, segera pesan makanan favorit antum</p>
              <router-link to="/" class="btn btn-lg btn-success mt-3">
                <b-icon-arrow-right> </b-icon-arrow-right> Pesan</router-link
              >
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Hero",
};
</script>

<style>
</style>