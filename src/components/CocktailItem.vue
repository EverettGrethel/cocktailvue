<template>
    <li @click='showModal'>
        <img :src="cocktail.strDrinkThumb">
        <h2>{{cocktail.strDrink}}</h2>
        <h3>Ingredients:</h3>
        <p>{{cocktail.strMeasure1 + " " + cocktail.strIngredient1}}</p>
        <p>{{cocktail.strMeasure2 + " " + cocktail.strIngredient2}}</p>
        <p>{{cocktail.strMeasure3 + " " + cocktail.strIngredient3}}</p>
        <p>{{cocktail.strInstructions}}</p>
    </li>
</template>

<script>
export default {
  name: 'cocktailitem',
  props: {
    msg: String,
    cocktail: Object,
    index: Number
  },
  methods: {
      showModal: function() {
          console.log('click');
          this.$emit('showModal', this.cocktail);
        }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
img {
    max-width: 50px;
}

li {
    list-style-type: none;
    background: #fff;
    border-radius: 2px;
    height: 200px;
    margin: 1rem;
    position: relative;
    box-shadow: 0 3px 6px rgba(0,0,0,0.16), 0 3px 6px rgba(0,0,0,0.23);
    padding: 20px;
}


</style>