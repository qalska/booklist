<template>
  <div id="app">
    <h1>List of books</h1>
    <BooksList
    v-if="books.lenght"
    v-bind:books="books"
    />
    <p v-else>No books!</p>
  </div>
</template>

<script>
import BooksList from '@/components/BooksList'

export default {
  name: 'App',
  components: {
    BooksList
  },
  data() {
    return {
      books: []
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
      .then(response => response.json())
      .then(json => {
        this.todos = json
      })
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>
