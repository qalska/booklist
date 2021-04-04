<template>
  <div id="app">
    <h1>BooksList</h1>

    <router-view />
  </div>
</template>

<script>
import BooksList from '@/components/BooksList'
import AddBook from '@/components/AddBook'

export default {
  name: 'app',
  data() {
    return{
      books: [
        {id: 1, title: 'Пример', author:'Списка', completed: false}
      ]
    }
  },
  methods: {
    removeBook(id) {
      this.books = this.books.filter(t => t.id !== id)
    },
    addBook(book) {
      this.books.push(book)
    }
  },
  components: {
    BooksList, AddBook
  }

}
</script>


<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
}
</style>
