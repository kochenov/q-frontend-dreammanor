<template>
  <q-tabs align="left" class="bg-primary text-white">
    <q-route-tab
      v-for="item in submenu[
        $route.query.submenu ? $route.query.submenu : 'home'
      ]"
      :key="item.id"
      :to="item.name"
      :label="item.label"
    />
  </q-tabs>
</template>

<script setup>
import { ref, onMounted } from "vue";
import axios from "axios";
const submenu = ref("");

onMounted(() => {
  axios
    .get("/data/submenu-nav.json")
    .then((response) => {
      submenu.value = response.data;
    })
    .catch((error) => {
      console.error("Ошибка при получении данных", error);
    });
});
</script>

<style lang="scss" scoped></style>
