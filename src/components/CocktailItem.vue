<template>
    <li @click='showModal'>
        <img :src="cocktail.strDrinkThumb">
        <h2>{{cocktail.strDrink}}</h2>
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
    width: 100%;
}

li {
    list-style-type: none;
    background: #fff;
    border-radius: 2px;
    margin: 1rem;
    position: relative;
    box-shadow: 0 3px 6px rgba(0,0,0,0.16), 0 3px 6px rgba(0,0,0,0.23);
    padding: 20px;
    text-align: center;
}

h2 {
  font-size: 20pt;
}


</style>