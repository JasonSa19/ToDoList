<script setup>
import { ref, onMounted, computed, watch } from "vue";

const toDos = ref([]);
const name = ref("");
const inputContent = ref("");
const inputCategory = ref(null);

const ToDoAsc = computed(() =>
  toDos.value.sort((a, b) => {
    return b.createdAt - a.createdAt;
  })
);
</script>

<template>
  <main id="app">
    <section class="greeting">
      Hey <input type="text" v-model="name" placeholder="Name eintragen" />
    </section>
  </main>
</template>

<style lang="scss">
@import "./assets/scss/style.scss";
</style>
