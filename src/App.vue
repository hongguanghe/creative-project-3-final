<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg">
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item"><img id="nav-icon" src="images\nav-icon\1.png" alt= "home"/><router-link to="/" class="nav-link">Home</router-link></li>
          <li class="nav-item"><img id="nav-icon" src="images\nav-icon\2.png" alt= "recipes"/><router-link to="/Categories" class="nav-link">Categories</router-link></li>
          <li class="nav-item"><router-link to="/" class="navbar-brand"><h1 id="navagation-title">Recipes</h1></router-link></li>
          <li class="nav-item"><img id="nav-icon" src="images\nav-icon\3.png" alt= "favorite"/><router-link to="/Favorite" class="nav-link">Favorite</router-link></li>
          <li class="nav-item"><img id="nav-icon" src="images\nav-icon\4.png" alt= "basket"/><router-link to="/Basket" class="nav-link">Basket</router-link></li>
        </ul>
      </div>
    </nav>
    <router-view />
  </div>
</template>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#navbarNav{
  display: flex;
  align-self: center;
  justify-content: center;
}

#nav-icon{
  width: 20px;
}

.navbar-nav{
  align-items: baseline;
}

a{
  color:black;
}

.navbar-brand{
  font-family:'Dancing Script';
  font-size: 45px;
  justify-content: center;
  margin: auto 40px;
  font-weight: bold;
}

.nav-item{
  display: flex;
  flex-direction: row;
  align-items: baseline;
  margin: 0px 20px;
}

</style>
