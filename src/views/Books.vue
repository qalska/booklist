<template>
  <div>
    <h2>Create new book!</h2>
    <AddBook 
      @add-book="addBook"
    />
    <hr>
    <BooksList
      v-if="books.length"
      v-bind:books="books"
      @remove-book="removeBook"
    />
    <p v-else>No books!</p>
    <router-link to="/create" class="btn">Create</router-link>
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

<style scoped>
  .btn {
    font-size: 36px;
    background: #ccc;
    border: 2px #aaa solid;
    border-radius: 5px;
    padding: .5rem 2rem;
    font-weight: bold;
    text-decoration: none;
    color: black;
    margin-top: 100px;
  }
</style>