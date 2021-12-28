<template>
  <div
    class="w-full h-full border-none max-w-sm bg-white shadow-xl rounded-xl overflow-hidden text-gray-900 md:pb-3 md:w-full md:h-full"
  >
    <div class="md:min-h-0">
      <img
        :src="`/images/${item.slug}.png`"
        alt="image not found"
        class="object-cover rounded-br-3xl max-h-[185px] lg:rounded-br-none md:w-full md:h-auto"
      />
    </div>
    <div
      class="w-full h-full relative px-2 py-5 md:px-4 grid flex-rows content-between"
    >
      <div class="h-full">
        <div class="flex tn:pt-2 items-center mb-1 md:mb-2 md:px-2">
          <img :src="`/icons/${item.slug}.svg`" alt="#" class="w-8 ml-1" />
          <h1 class="md:text-2xl font-bold mx-2">{{ item.name }}</h1>
        </div>
        <div
          v-for="(data, id) in item.packages"
          :key="id"
          class="tn:px-1 tn:py-1 md:px-2 md:mt-3 lg:px-4"
        >
          <div class="text-xl md:text-lg md:flex md:justify-between mt-1">
            <p class="font-semibold md:font-normal">
              {{ data.name }}
            </p>
            <div class="flex font-bold">
              <div>Rp {{ formatPrice(data.price) }}</div>
              <div class="text-xl font-light">
                <div v-if="data.type === 'monthly'">/bln</div>
                <div v-else>/thn</div>
              </div>
            </div>
          </div>
        </div>
        <p
          class="text-2xl text-green-400 py-4 md:text-xl md:px-2 lg:px-4 font-bold text-primary my-2 cursor-pointer"
        >
          Lihat skema harga
        </p>
      </div>
      <div class="h-full sticky bottom-0">
        <div class="md:px-2">
          <div class="h-px w-full bg-primary md:my-3"></div>
        </div>
        <div class="text-center border-t-4 border-green-400 py-5 md:px-2">
          <Button content="pesan" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Button from "~/components/atoms/Button";
export default {
  components: { Button },
  props: {
    item: {
      type: Object,
      default: {},
    },
    packages: {
      type: Object,
      default: {},
    },
  },
  methods: {
    formatPrice(value) {
      let val = (value / 1).toFixed(2).replace(".", ",");
      return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
    },
  },
};
</script>

<style></style>
