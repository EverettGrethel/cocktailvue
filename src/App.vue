<template>
  <div id="app">
    <cocktailsearch v-on:search-item="searchItem" />
    <ul>
      <cocktailitem
          v-for="(cocktail, index) in items"
          v-bind:key="cocktail.idDrink"
          v-bind:cocktail="cocktail"
          v-bind:index="index"
          v-on:showModal="showModal"
      ></cocktailitem>
    </ul>
    <modal
      v-show="isModalVisible"
      @close="closeModal"
      v-bind:strDrink="strDrink"
      v-bind:strIngredient1="strIngredient1"
      v-bind:strIngredient2="strIngredient2"
      v-bind:strIngredient3="strIngredient3"
      v-bind:strMeasure1="strMeasure1"
      v-bind:strMeasure2="strMeasure2"
      v-bind:strMeasure3="strMeasure3"
      v-bind:strInstructions="strInstructions"
    />
  </div>
</template>

<script>
import cocktailitem from '@/components/CocktailItem.vue'
import cocktailsearch from '@/components/CocktailSearch.vue'
import modal from './components/Modal.vue'

export default {
  components: { cocktailsearch, cocktailitem, modal },
  data: function() {
    return {
      item: "",
      items: [],
      isModalVisible: false,
      strDrink: "Margarita",
      strIngredient1: "coconut",
      strIngredient2: "banana",
      strIngredient3: "whiskey",
      strMeasure1: "1 oz",
      strMeasure2: "2 oz",
      strMeasure3: "3 oz",
      strInstructions: "Shake it a lot!"
    }
  },
  methods: {
    searchItem: function(item) {
      console.log("hello!");
      fetch(`https://www.thecocktaildb.com/api/json/v1/1/search.php?s=${item}`)
      .then(response => response.json())
      .then(data => {
        console.log(data);
        data = data['drinks'];
        this.items = data;
        console.log(this.items);
      });
    },
    showModal(cocktail) {
        this.strDrink = cocktail.strDrink;
        this.strIngredient1 = cocktail.strIngredient1;
        this.strIngredient2 = cocktail.strIngredient2;
        this.strIngredient3 = cocktail.strIngredient3;
        this.strMeasure1 = cocktail.strMeasure1;
        this.strMeasure2 = cocktail.strMeasure2;
        this.strMeasure2 = cocktail.strMeasure3;
        this.strInstructions = cocktail.strInstructions;
        this.isModalVisible = true;
    },
    closeModal() {
      this.isModalVisible = false;
    }
  },
};
</script> 

<style>
* {
  padding: 0;
  margin: 0;
}

ul {
  width: 100%;
  display: grid;
  grid-auto-flow: row;
  grid-template-columns: repeat(4, 1fr);
}
</style>