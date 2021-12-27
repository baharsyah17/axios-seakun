<template>
  <button
    type="button"
    variant="primary"
    label="Pesan"
    class="w-full bg-green-200 rounded-lg py-2 my-2 font-bold btn btn-primary"
  >
    <div>{{ content }}</div>
  </button>
</template>

<script>
export default {
  props: {
    content: {
      type: String,
      default: "Submit",
    },
  },
};
</script>

<style></style>
