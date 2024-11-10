<template>
  <h6>Filtros</h6>
  <div class="category-filter">
    <q-select label="Categoría" v-model="model" filled :options="categories" />
  </div>
  <div class="price-filter">
    <label>Rango de precios</label>
    <q-input
      class="precios"
      v-model="minimo"
      filled
      type="number"
      label="Mínimo"
    />
    <q-input
      class="precios"
      v-model="maximo"
      filled
      type="number"
      label="Máximo"
    />
  </div>
</template>

<style></style>

<script>
export default {
  name: "ProductFilter",
  data() {
    return {
      minimo: 0,
      maximo: 0,
      model: null,
      categories: ["Celulares", "Televisores", "Laptops"],
    };
  },
};
</script>
