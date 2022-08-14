<script setup>
import { ref, watch, onMounted } from "vue";

const count = ref(0);

watch(count, (newVal) => {
  localStorage.setItem("count", newVal);
});

onMounted(() => {
  count.value = localStorage.getItem("count") || "";
});
</script>

<template>
  <h1>Count App</h1>
  <section>
    <input
      type="number"
      placeholder="amount here"
      v-model="count"
      v-if="count >= 0"
    />
  </section>
  <div class="counter">
    <button type="button" @click="count++" v-if="count >= -1">+</button>
    <button type="button" @click="count--" v-if="count > 0">-</button>

    <h2>{{ count }}</h2>
  </div>
</template>
