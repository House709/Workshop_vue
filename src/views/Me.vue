<template>
  <v-app-bar width="full" height="1000">
    <v-col>
      <v-row align="center" justify-center>
        <div class="card">
          <golangcard />
          <div class="card-detail">
            <div v-for="(item, index) in items" :key="index">
              <p>{{ item }}</p>
            </div>
          </div>
        </div>
      </v-row>
    </v-col>
  </v-app-bar>
</template>

<script>
import golangcard from "../components/CardImg.vue";
export default {
  components: {
    golangcard,
  },
  data() {
    return {
      items: [
        "ชื่อเล่น: นิ้ง",
        "มหาวิทยาลัย: มหาวิทยาลัยเชียงใหม่",
        "สาขา: คณิตศาสตร์",
        "งานอดิเรก: ฟังเพลง เล่นเกม ดูอนิเมะ",
        "สิ่งที่ชอบ: นมสดโอริโอ้ปั่น",
        "สิ่งที่ไม่ชอบ: ฤดูร้อน",
      ],
    };
  },
};
</script>

<style>
p {
  border-radius: 20px;
  padding: 5px;
  font-size: 18px;
}

.card {
  background-color: azure;
  border: 2px solid silver;
  border-radius: 20px;
  box-shadow: 6px 6px 5px gray;
  text-shadow: 5px 5px 5px gray;
  width: 1000px;
  height: 400px;
  display: flex;
  flex-direction: row;
  margin: 10px;
  justify-content: center;
  align-items: center;
  gap: 30px;
}
</style>
