<template>
  <div id="home">
    <h1>Cocktail Search!</h1>
    <form class="searchForm" @submit.prevent="searchItem">
      <p>
          <label for="item">Search:</label>
          <input v-model="item">
      </p>
      <button>Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'cocktailsearch',
  data: function() {
    return {
      item: ""
    }
  },
  props: {
    msg: String
  },
  methods: {
      searchItem: function() {
          this.$emit('search-item', this.item);
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#home {
  display: flex;
  align-items: center;
  flex-direction: column;
}

h1 {
  padding-top: 25px;
}

form {
  padding: 25px;
}

button {
  margin-top: 10px;
  padding: 5px;
}


</style>