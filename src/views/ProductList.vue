<template>
  <div class="container">
    <v-row>
      <v-col
        col="12"
        sm="6"
        md="4"
        lg="3"
        v-for="product in products"
        :key="product._id"
      >
        <ProductCard :product="product" /> </v-col
    ></v-row>
  </div>
</template>

<script>
import ProductCard from "@/components/ProductCard.vue";
import Config from "../config";
export default {
  data() {
    return {
      products: [],
    };
  },
  created() {
    this.getProducts();
  },
  components: {
    ProductCard,
  },
  methods: {
    async getProducts() {
      try {
        const response = await this.axios.get(Config.base_url + "/products");
        this.products = response.data.data;
        console.log(this.products);
      } catch (error) {
        console.error("Error fetching products:", error);
      }
    },
  },
};
</script>

<style></style>
