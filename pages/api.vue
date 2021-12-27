<template>
  <div class="w-full h-full flex items-center p-28">
    <div
      class="w-full h-full grid xl:grid-cols-4 grid-cols-2 lg:grid-cols-3 gap-2 md:gap-4 lg:gap-6 xl:gap-6 px-0 justify-center"
    >
      <APICard v-for="(item, id) in packets" :key="id" :item="item" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import APICard from "../components/mollecules/APICard.vue";

export default {
  components: { APICard },
  data() {
    return {
      packets: [],
    };
  },
  mounted() {
    this.getDataFromSeakun();
  },
  methods: {
    getDataFromSeakun() {
      var api = "https://seakun-packet-api-v2.herokuapp.com/product-digital";
      axios
        .get(api)
        .then((res) => {
          this.packets = res.data;
          console.log(this.packets);
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style></style>
