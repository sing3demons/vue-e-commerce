<template>
  <div class="home">
    <section class="hero is-medium is-dark mb-6">
      <div class="hero-body has-text-centered">
        <p class="title mb-6">
          Welcome to sing3demons
        </p>
        <p class="subtitle">
          The best sing3demons store online
        </p>
      </div>
    </section>

    <div class="columns is-multiline">
      <div class="column is-12">
        <h2 class="is-size-2 has-text-centered">Latest products</h2>
      </div>

      <ProductBox
        v-for="product in latestProducts"
        v-bind:key="product.id"
        v-bind:product="product"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import ProductBox from "@/components/ProductBox";
export default {
  name: "Home",
  components: {
    ProductBox,
  },
  data: () => ({
    latestProducts: [],
  }),
  mounted() {
    this.getLatestProducts();
  },
  methods: {
    async getLatestProducts() {
      const { data } = await axios.get("/api/v1/latest-products/");
      this.latestProducts = data;
    },
  },
};
</script>
<style scoped>
.image {
  margin-top: -1.25rem;
  margin-left: -1.25rem;
  margin-right: -1.25rem;
}
</style>
