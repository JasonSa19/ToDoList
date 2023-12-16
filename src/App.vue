<script setup>
import { ref, onMounted, computed, watch } from "vue";

// Empty Array for ToDos
const toDos = ref([]);
// Empty String for Name

const name = ref("");

// Empty String for ToDo
const inputContent = ref("");

// Empty const for category
const inputCategory = ref(null);

// ToDo Sorting in List
const ToDoAsc = computed(() =>
  toDos.value.sort((a, b) => {
    return b.createdAt - a.createdAt;
  })
);

// Live Watch for Name Input
watch(name, (newVal) => {
  localStorage.setItem("name", newVal);
});

onMounted(() => {
  name.value = localStorage.getItem("name") || "";
});

// Pull name from Local Storage
</script>

<template>
  <main id="app">
    <section class="greeting mt-12 flex justify-center">
      <h2 class="font-bold">
        Hey
        <input
          class="appearance-none border-none bg-transparent text-white focus:border-none"
          type="text"
          placeholder="Name eintragen"
          v-model="name"
        />
      </h2>
    </section>
  </main>
</template>

<style lang="scss">
@import "./assets/scss/style.scss";
</style>
