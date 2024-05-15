<template>
  <div class="container">
    <v-sheet class="mx-auto" width="300">
      <v-form @submit.prevent="addProduct">
        <v-text-field
          v-model="newProduct.product_name"
          :rules="productNameRules"
          label="Product name"
        ></v-text-field>

        <v-text-field
          v-model="newProduct.price"
          :rules="priceRules"
          label="Price"
        ></v-text-field>

        <v-text-field
          v-model="newProduct.amount"
          :rules="amountRules"
          label="Amount"
        ></v-text-field>

        <v-file-input
          v-model="newProduct.product_image"
          :rules="imageRules"
          accept="image/png, image/jpeg, image/bmp"
          label="Product image"
          placeholder="Pick an image"
          prepend-icon="mdi-camera"
        ></v-file-input>

        <v-btn
          color="success"
          class="mt-2"
          type="submit"
          block
          :disabled="!isFormValid"
          >Submit</v-btn
        >
      </v-form>
    </v-sheet>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newProduct: {
        product_name: "",
        price: null,
        amount: null,
        product_image: null,
      },
      productNameRules: [(v) => !!v || "Product name is required"],
      priceRules: [
        (v) => !!v || "Price is required",
        (v) => /^\d*\.?\d*$/.test(v) || "Price must be a valid number",
        (v) => v > 0 || "Please input price more than 0",
      ],
      amountRules: [
        (v) => !!v || "Amount is required",
        (v) => /^\d*\.?\d*$/.test(v) || "Amount must be a valid number",
        (v) => v > 0 || "Please input amount more than 0",
      ],
      imageRules: [(v) => !!v || "Image is required"],
    };
  },
  computed: {
    isFormValid() {
      return (
        this.newProduct.product_name &&
        this.newProduct.price &&
        this.newProduct.amount &&
        this.newProduct.product_image &&
        this.newProduct.amount > 0 &&
        this.newProduct.price > 0 &&
        /^\d*\.?\d*$/.test(this.newProduct.price) &&
        /^\d*\.?\d*$/.test(this.newProduct.amount)
      );
    },
  },
  methods: {
    async addProduct() {
      try {
        const formData = new FormData();
        formData.append("product_name", this.newProduct.product_name);
        formData.append("price", this.newProduct.price);
        formData.append("amount", this.newProduct.amount);
        formData.append("product_image", this.newProduct.product_image);

        const response = await this.axios.post(
          "http://localhost:3000/products",
          formData
        );
        if (response.status === 201) {
          alert("Product added successfully");
          this.clearForm();
          window.location.reload();
        } else {
          throw new Error("Failed to add product");
        }
      } catch (error) {
        console.error("Error adding product:", error);
        alert("Failed to add product");
      }
    },
    clearForm() {
      this.newProduct.product_name = "";
      this.newProduct.price = null;
      this.newProduct.amount = null;
      this.newProduct.product_image = null;
    },
  },
};
</script>

<style></style>
