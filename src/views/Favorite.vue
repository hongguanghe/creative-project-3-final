<template>
  <div class="main">
    <div class="title">
      <h1>Favorite List</h1>
    </div>
    <h1 id="emptyWarning" v-if="currentFavorite.length === 0">No Recipes Found!</h1>
    <div v-else>
      <!-- <favoriteList  :recipe="currentFavorite" />
      <RecipeList :recipes = "recipes" /> -->
      <ul class="recipesList">
        <li class="everyItem">
        <div v-for="favorite in this.$root.$data.favorite" :key="favorite.id" class="singleRecipe">
          <div class="pic-favorite">
            <img :src= "'/images/recipes/'+favorite.image" id="recipeImg"/>
          </div>
          <div class="info">
            <div class="info-header">
              <div id="name">{{favorite.name}}</div>
            </div>
            <!-- <div class="favorite-button">
              <p @click="addToFavorite(recipe)"> </p>
            </div> -->
            <div class="infoSection">
              <div class="someInfo">
                  <ul id="info-no-style">
                    <li><span id="boldFont">Category:</span> {{favorite.category}} </li>
                    <li><span id="boldFont">Calories:</span> {{favorite.calories}}</li>
                    <li><span id="boldFont">Time Needed:</span> {{favorite.time}}</li>
                    <!-- <div id="addToFavoriteText" @click="addToFavorite(recipe)">
                      <p><img id="nav-icon" src="images\nav-icon\3.png" alt= "favorite"/> Add to Favorite</p>
                    </div> -->
                    <li>
                      <div class="removeButton">
                      <div @click="remove(favorite)"><img id="nav-icon" src="images\nav-icon\4.png" alt= "basket"/> Remove</div>
                      </div>
                    </li>
                  </ul>
              </div>
              <div class="ingredientList">
                <ul v-for="ingredient in getRecipes(favorite)" :key="ingredient" id="oneIngridient">
                  <li>{{ingredient}} </li>
                  <!-- <li>{{ingredient}}  <span @click="addToBasket(ingredient)><p>add to basket</p></span></li> -->
                </ul>
              </div>
            </div>

          </div>

        </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
   // import favoriteList from '../components/FavoriteList.vue'
  // import RecipeList from "../components/RecipeList.vue"

  export default{
    name: 'Favorite',
    components: {
      // favoriteList,
      // RecipeList
    },
    methods:{
      getRecipes(favorite){
        return favorite.ingredients;
      },
      remove(favorite){
        this.$root.$data.favorite.splice(this.$root.$data.favorite.lastIndexOf(favorite,1));
      },
    },
    computed: {
      currentFavorite(){
        let object = {};
        for (let i = 0; i < this.$root.$data.favorite.length; i++) {
          let id = this.$root.$data.favorite[i].id;
          if (id in object) {
            // object[id].quantity += 1;
          }
          else {
            object[id] = this.$root.$data.favorite[i];
          }
        }
        return Object.values(object);
      }
    },
  }

</script>

<style scoped>
  #emptyWarning{
    text-align: center;
    font-size: 100px;
    padding-top:50px;
    border-top: 1px solid #C2C2C2;
  }
  .main {
    /* max-width: 70%; */
    margin: 0 auto;
  }

  .title {
    display: flex;
    justify-content: center;
    flex-direction: column;
    padding-bottom: 10px;
    /* border-bottom: 1px solid #C2C2C2; */
  }
  #recipeImg{
    width: 200px;
    height: 200px;
    margin-right: 50px;
   }
  .recipesList{
    list-style: none;
    padding: 0;
    list-style-type: none;
  }
  .singleRecipe{
    border-top: 1px solid #C2C2C2;
    padding-top:30px;
    margin: 10px;
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
  .removeButton{
    padding-top: 20px;
  }
</style>
