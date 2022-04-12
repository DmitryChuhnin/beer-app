<template>
  <div class="beer-recomendation">
    <div class="beer">
        <p class="beer-name">{{beerName}}</p>
        <div class="beer-characters">
            <p>{{brand}}</p>
            <p>{{style}}</p>
            <p>{{ibu}}</p>
            <p>{{alcohol}}</p>
        </div>
    </div>
    <div class="buttons">
      <button id="next" @click="getBeer()">
        Next
      </button>
    </div>
  </div>
 
</template>

<script>
export default {
  name: 'BeerRecomendation',
  components: {
   
  },
  data() {
    return {
      beerName: 'John',
      style: 'Test',
      brand: 'beer',
      ibu: '20',
      alcohol: 'name',
    }
  },
  methods: {
    async getBeer() {
      const res = await fetch('https://random-data-api.com/api/beer/random_beer')
      const result = await res.json()


      this.beerName = result.name
      this.style= result.style
      this.brand = result.brand
      this.ibu = result.ibu
      this.alcohol = result.alcohol
    },
    
  },
}
</script>

<style>
.beer-recomendation{
    width: 60%;
    background-color: #FFF;
    color: #000;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;

}
.beer-name{
    font-size: 2rem;
    font-weight: 600;
}
.beer-characters{
    text-align: center;
}
#next{
  padding: 15px 25px;
  background-color: transparent;
  font-weight: 600;
  font-size: 1rem;
  border: 3px solid rgb(51, 51, 51);
  transition: all 0.2s ease-in-out;

}
#next:hover{
  background-color: rgb(219, 219, 219);
}
@media (max-width: 800px) {
  .beer-recomendation{
    width: 100%;
    padding: 20px;
  }
}

</style>