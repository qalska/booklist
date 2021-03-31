<template>
    <div>
        <ul>
            <BooksListItem 
                v-for="(book, index) of books"
                v-bind:key="index"
                v-bind:book="book"
                v-on:remove-book="removeBook"
            />
        </ul>
    </div>
</template>

<script>
import BooksListItem from "@/components/BooksListItem"
export default {
    props: ['books'],
    components: {
        BooksListItem
    },
    methods: {
        removeBook(id) {
            this.$emit('remove-book', id)
        }
    }
}
</script>

<style scoped>
    ul {
        list-style: none;
        margin: 0;
        padding: 0;
    }
</style>