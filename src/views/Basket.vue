<template>
  <div class="main">
    <div class="title">
      <h1>Basket</h1>
    </div>
    <h1 id="emptyWarning" v-if="currentBasket.length == 0">No Items Found!</h1>
    <div v-else>
      <ul class="recipesList">
        <li class="everyItem">
        <div v-for="item in this.$root.$data.basket" :key="item.id" class="singleRecipe">
          <div class="info">
            <div id="name">{{item.name}}</div>
            <div class="itemQuantity">Quantities: {{item.quantity}}</div>
            <div class="buttonGroup">
              <button type="button" @click="add(item.id)" name="increment" id="incrementButton">+</button>
              <button type="button" @click="minus(item.id)" name="remove">-</button>
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
    name: 'Basket',
    components: {
      // favoriteList,
      // RecipeList
    },
    methods:{
      add(id){
        this.$root.$data.basket[id].quantity += 1;
      },
      minus(id){
        this.$root.$data.basket[id].quantity -= 1;
        if (this.$root.$data.basket[id].quantity == 0){
          this.$root.$data.basket.splice(this.$root.$data.basket.lastIndexOf(this.$root.$data.basket[id]),1);
        }
      }
    },
    computed: {
      currentBasket(){
        let object = {};
        for (let i = 0; i < this.$root.$data.basket.length; i++) {
          let id = this.$root.$data.basket[i].id;
          if (id in object) {
            // object[id].quantity += 1;
          }
          else {
            object[id] = this.$root.$data.basket[i];
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
    align-items: baseline;
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

  .itemQuantity{
    padding-left: 50px;
  }
  #incrementButton{
    margin-right: 20px;
  }
  .info{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: baseline;
  }
  .buttonGroup{
    right:15%;
    position: absolute;
  }
</style>
