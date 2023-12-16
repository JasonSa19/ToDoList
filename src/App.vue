<script setup>
import { ref, onMounted, computed, watch } from "vue";
import dayjs from "dayjs";

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

// get storaged Name
onMounted(() => {
  name.value = localStorage.getItem("name") || "";
});

const currentDate = new Date().toISOString();
const formatDate = (currentDate) => {
  const formattedDate = dayjs(currentDate).format("DD.MM.YYYY");
  return formattedDate;
};

const finalDate = formatDate(currentDate);
</script>

<template>
  <main id="app">
    <section class="greeting mt-12 flex justify-center">
      <div class="intro flex flex-col text-center align-middle">
        <h2 class="text-center font-bold">
          ToDo-Liste von
          <input
            class="appearance-none border-none bg-transparent text-white focus:border-none"
            type="text"
            placeholder="Name eintragen"
            v-model="name"
          />
        </h2>
        <h3 class="mt-6">{{ finalDate }}</h3>
      </div>
    </section>
  </main>
</template>

<style lang="scss">
@import "./assets/scss/style.scss";
</style>
