<template>
  <ul class="recipesList">
    <li class="everyItem">
    <div v-for="recipe in recipes" :key="recipe.id" class="singleRecipe">
      <div class="pic-favorite">
        <img :src= "'/images/recipes/'+recipe.image" id="recipeImg"/>
      </div>
      <div class="info">
        <div class="info-header">
          <div id="name">{{recipe.name}}</div>
        </div>
        <!-- <div class="favorite-button">
          <p @click="addToFavorite(recipe)"> </p>
        </div> -->
        <div class="infoSection">
          <div class="someInfo">
              <ul id="info-no-style">
                <li><span id="boldFont">Category:</span> {{recipe.category}} </li>
                <li><span id="boldFont">Calories:</span> {{recipe.calories}}</li>
                <li><span id="boldFont">Time Needed:</span> {{recipe.time}}</li>
                <div id="addToFavoriteText" @click="addToFavorite(recipe)">
                  <p><img id="nav-icon" src="images\nav-icon\3.png" alt= "favorite"/> Add to Favorite</p>
                </div>
              </ul>
          </div>
          <div class="ingredientList">
            <ul v-for="ingredient in getRecipes(recipe)" :key="ingredient" id="oneIngridient">
              <!-- <li>{{ingredient}} </li> -->
              <li class="line">
                <div class="indivual">
                  {{ingredient}}
                </div>
                <div class="addToBasketText">
                  <div @click="addToBasket(ingredient)"><img id="nav-icon" src="images\nav-icon\4.png" alt= "basket"/></div>
                </div>
              </li>

            </ul>
          </div>
        </div>

      </div>

    </div>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'RecipesList',
  props: {
    recipes: Array
  },
  methods: {
    addToFavorite(recipe){
      if (this.$root.$data.favorite.length != 0){
        for (let i = 0; i < this.$root.$data.favorite.length; i++) {
          if (recipe == this.$root.$data.favorite[i]){
            alert("Already in the Favorite!");
            break;
          }
          else{
            if (i == this.$root.$data.favorite.length - 1){
              this.$root.$data.favorite.push(recipe);
              alert("Just added it!");
              break;
            }
            else {
              continue;
            }
          }
        }
      }
      else {
        this.$root.$data.favorite.push(recipe);
        alert("Just added it!");
      }

    },
    getRecipes(recipe){
      return recipe.ingredients;
    },
    addToBasket(product){
      // debugger;
      let newProduct = {
        id: this.$root.$data.basket.length ,
        name: product.toString(),
        quantity: 1,
      }
      if (this.$root.$data.basket.length == 0) {
        this.$root.$data.basket.push(newProduct);
        alert("Just added it to basket!");
      }
      else {
        for (let i = 0; i < this.$root.$data.basket.length; i++) {
          let name = this.$root.$data.basket[i].name;
          if (name == product) {
            this.$root.$data.basket[i].quantity += 1;
            alert("Just added it to basket!");
            break;
          }
          else {
            if (i == this.$root.$data.basket.length - 1){
              this.$root.$data.basket.push(newProduct);
              alert("Just added it to basket!");
              break;
            }
            else {
              continue;
            }
          }
        }
      }
    }
  }
}
</script>

<style scoped>
  #recipeImg{
    width: 200px;
    height: 200px;
    margin-right: 50px;
   }
  .recipesList{
    list-style: none;
    padding: 0;
    list-style-type: none;
    width:100%;
  }
  .singleRecipe{
    border-top: 1px solid #C2C2C2;
    padding-top:30px;
    margin: 10px;
    /* display: flex;
    justify-content: space-between; */
  }
  #nav-icon{
    width:15px;
    height:15px;
    /* margin-left: 20px; */
  }

  .everyItem{
    display: flex;
    flex-direction: column;
  }
  .singleRecipe{
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    width:100%;
  }
  #name{
    text-align: left;
    font-weight: bold;
    font-size: 25px;
  }
  #oneIngridient{
    padding:0px;
    text-align: left;
  }
  .info-header{
    display: flex;
    justify-content: space-between;
    flex-direction: row;
    margin-bottom: 20px;
  }
  .infoSection{
    display: flex;
    flex-direction: row;
  }
  #boldFont{
    font-weight: bold;
  }
  .someInfo{
    margin-right: 30px;
  }
  #info-no-style{
    text-align: left;
    list-style-type: none;
    padding-left: 0;
  }
  #addToFavoriteText{
    padding-top: 20px;
  }
  .line{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
  .info{
    display: flex;
    justify-content: space-between;
    flex-direction: column;
  }
  .addToBasketText{
    right: 15%;
    position: absolute;
  }
</style>
