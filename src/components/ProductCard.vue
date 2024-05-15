<template>
  <v-card
    class="mx-auto my-8"
    elevation="16"
    max-width="230
  "
  >
    <v-card-item>
      <v-card-title
        ><img
          :src="base_url + product.product_image"
          :alt="product.product_name"
          width="200"
          height="200"
          class="img"
        />
      </v-card-title>
    </v-card-item>

    <v-card-text>
      <p>Name:&nbsp; {{ product.product_name }}</p>
      <p>Price:&nbsp; {{ product.price }}</p>
      <p>Amount:&nbsp; {{ product.amount }}</p>
      <v-btn variant="tonal" color="blue" class="d-flex">
        <img src="../assets/cart.png" alt="Cart" width="25" height="25" />
        &nbsp;&nbsp;เพิ่มสินค้า
      </v-btn>
    </v-card-text>
  </v-card>
</template>

<script>
import Config from "../config";
export default {
  data() {
    return {
      base_url: Config.base_url,
    };
  },
  props: {
    product: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style></style>
