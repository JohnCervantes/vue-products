<template>
  <div class="bg-yellow-300 h-screen w-screen">
    <p class="text-center text-5xl">Products</p>
    <div class="flex items-center justify-center">
      <div class="grid grid-cols-4 gap-1">
        <div v-for="data in data.data" :key="data.id">
          <img :src="data.image" :alt="data.catdescription" />
          <div class="bg-black text-white text-center">
            <p>{{ data.name }}</p>
            <p>${{ data.price }}.00</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
import axios from "axios";

export default {
  name: "Posts",
  props: {},
  setup() {
    const data = ref([]);
    const loading = ref(true);
    const error = ref(null);

    onMounted(async () => {
      const res = await axios.get(
        "https://trayvonnorthern.com/Edgewood-API/public/api/products"
      );
      data.value = res.data;
    });

    return {
      data,
      loading,
      error,
    };
  },
};
</script>
