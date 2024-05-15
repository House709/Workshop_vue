<template>
  <div>
    <v-app-bar app color="primary" dark>
      <router-link to="/products">
        <v-btn color="white" text>
          <span class="mr-2">Shoppo</span>
        </v-btn>
      </router-link>
      <v-spacer></v-spacer>

      <router-link to="products/create">
        <v-btn color="red">
          <span class="mr-2">Create Product</span>
        </v-btn>
      </router-link>
    </v-app-bar>
    <v-main>
      <router-view />
    </v-main>
  </div>
</template>

<script>
export default {};
</script>

<style></style>
