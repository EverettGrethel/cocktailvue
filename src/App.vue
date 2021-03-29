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
      strDrink: "Margarita"
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