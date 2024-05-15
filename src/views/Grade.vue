<template>
  <div class="container">
    <v-sheet class="mx-auto" width="300">
      <v-form fast-fail @submit.prevent>
        <v-text-field
          v-model="score"
          :rules="scoreRules"
          label="Score"
        ></v-text-field>

        <v-btn
          class="mt-2"
          type="submit"
          color="success"
          block
          @click="calculate"
          :disabled="
            !score ||
            score > 100 ||
            score < 0 ||
            isNaN(score) ||
            /^\+/.test(score)
          "
          >Submit</v-btn
        >
      </v-form>
    </v-sheet>
    <div class="grade">
      <h1>Grade:</h1>
      <h1>{{ grade }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      score: "",
      grade: "",
      scoreRules: [
        (v) => !!v || "Score is required",
        (v) => /^\d*\.?\d*$/.test(v) || "Score must be a valid number",
        (v) => (v <= 100 && v >= 0) || "Please input score 0 - 100",
      ],
    };
  },
  methods: {
    calculate() {
      if (this.score >= 80) {
        this.grade = "A";
      } else if (this.score >= 70) {
        this.grade = "B";
      } else if (this.score >= 60) {
        this.grade = "C";
      } else if (this.score >= 50) {
        this.grade = "D";
      } else {
        this.grade = "F";
      }
    },
  },
};
</script>

<style>
.grade {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-top: 15px;
  color: black;
}

.container {
  margin-top: 200px;
}
</style>
