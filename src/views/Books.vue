<template>
  <div>
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