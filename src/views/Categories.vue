<template>
<div class="main">
  <div class="filter-content">
    <h1>Filter by types of recipes</h1>
    <div class="pure-menu pure-menu-horizontal">
      <ul class="pure-menu-list">
        <li class="pure-menu-item"><a @click="select('Appetizer')" href="#" class="pure-menu-link">Appetizer</a></li>
        <li class="pure-menu-item"><a @click="select('Entree')" href="#" class="pure-menu-link">Entree</a></li>
        <li class="pure-menu-item"><a @click="select('Dessert')" href="#" class="pure-menu-link">Dessert</a></li>
        <li class="pure-menu-item"><a @click="select('Drink')" href="#" class="pure-menu-link">Drink</a></li>
      </ul>
    </div>
  </div>
  <RecipeList :recipes = "recipes" />
</div>
</template>

<script>
import RecipeList from "../components/RecipeList.vue"
export default {
  name: 'Categories',
  components: {
    RecipeList
  },
  data() {
    return {
      category: '',
    }
  },
  computed: {
    recipes() {
      if (this.category === ''){
        return this.$root.$data.recipes;
      }
      return this.$root.$data.recipes.filter(recipe => recipe.category === this.category);
    }
  },
  methods: {
    select(category) {
      this.category = category;
    }
  }
}
</script>

<style scoped>

  .filter-content{
    display: flex;
    flex-direction: row;
    justify-content:space-between;
  }

  .pure-menu.pure-menu-horizontal{
    margin-bottom: 0px;
    max-height: fit-content;
    align-self: center;
    text-align: right;
    max-width: fit-content;
  }

  .main{
    margin: 0 auto;
    /* width: 70%; */
  }

</style>
