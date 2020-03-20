<template>
  <div class="home">
    <h1>All Recipes</h1>
    <RecipesList :recipes = "recipes" />
  </div>
</template>

<script>
// @ is an alias to /src
import RecipesList from '@/components/RecipeList.vue'

export default {
  name: 'Home',
  components: {
    RecipesList
  },
  computed: {
    recipes(){
      return this.$root.$data.recipes;
    }
  },
}
</script>
