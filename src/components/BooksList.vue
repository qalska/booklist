<template>
    <div class="books">
        <ul class="bookslist">
            <BooksListItem/>
        </ul>
    </div>
</template>

<script>
import BooksListItem from '@/components/BooksListItem'

export default {
    props: ['books'],
    components: {
        BooksListItem
    }
}
</script>

<style scoped>
    ul{
        list-style: none;
        margin: 0;
        padding: 0;
    }
</style>
