<template>
  <div class="main">
    <div class="card">
      <Profile/>
      <BeerRecomendation/>
    </div>
    
  </div>
 
</template>

<script>
import Profile from "@/components/Profile"
import BeerRecomendation from "@/components/BeerRecomendation"
export default {
  name: 'App',
  components: {
   Profile,
   BeerRecomendation,
  }
}
</script>

<style>
:root{
  font-size: 18px;
}
body{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #8C6E6C;
  text-align: center;
}
#app {
  color: #2c3e50;
}
.main{
  width: 100vw; 
  display: flex;
  align-items: center;

}
.card{
  width: 80%;
  margin: 40px auto;
  background-color: #FFF;
  display: flex;
  flex-wrap: wrap;

}
@media (max-width: 800px) {
  :root{
    font-size: 16px;
  }
}
@media (max-width: 350px) {
  :root{
    font-size: 12px;
  }
}

</style>
