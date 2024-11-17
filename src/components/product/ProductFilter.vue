<template>
  <h6>Filtros</h6>
  <div class="category-filter">
    <q-select label="Categoría" v-model="categorySelected" filled :options="categories" option-value="id"
      option-label="description" @update:model-value="onChange" />
  </div>
  <div class="price-filter">
    <label>Rango de precios</label>
    <q-input class="precios" v-model="minimo" filled type="number" label="Mínimo" />
    <q-input class="precios" v-model="maximo" filled type="number" label="Máximo" />
  </div>
</template>

<style></style>

<script>
export default {
  name: "ProductFilter",
  emits: ["categoriaCambiada"],
  data() {
    return {
      minimo: 0,
      maximo: 0,
      model: null,
      categories: [],
      categorySelected: null
    };
  },
  mounted() {
    this.cargarCategorias();
  },
  methods: {
    onChange(value) {
      console.log("El valor seleccionado es: ", value.id)
      this.$emit("categoriaCambiada", value.id);
    },
    // Listar las categorias
    cargarCategorias() {
      let endpointURL = "/api/Category";
      this.$api.get(endpointURL)
        .then(response => {
          this.categories = response.data;
        })
        .catch(error => {
          console.error(error);
        });


    }
  }
};
</script>
