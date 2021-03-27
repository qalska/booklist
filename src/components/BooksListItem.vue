<template>
    <li class="bookslist-item">
        <span class="bookslist-span" v-bind:class="{done: book.completed}">
            <input type="checkbox" class="bookslist-status" v-on:change="book.completed=!book.completed">
            <div class="booklist-text">
                <span class="bookslist-author"></span>
                <span class="bookslist-title"></span>
            </div>
            <button class="bookslist-btn change"></button>
            <button class="bookslist-btn remove"></button>
        </span>
    </li>
</template>

<script>
export default {
    props: {
        book: {
            type: Object,
            required: true
        },
        index: Number
    }
}
</script>

<style lang="scss" scoped>
    @mixin flex_space-between () {
    display: flex;
    justify-content: space-between;
    align-items: center;
    }
    li {
        width: 75%;
        margin: 0 auto;
    }
    .bookslist{
        &-span{
            border: 2px #aaa solid;
            border-radius: 5px;
            @include flex_space-between();
            padding: .5rem 2rem;
            margin-bottom: 1rem;
        }
        &-text{
            @include flex_space-between();
        }
        &-btn{
            background: #ccc;
            border: 2px #aaa solid;
            border-radius: 5px;
            padding: .5rem 2rem;
            font-weight: bold;
        }
        &-status{
            margin-right: 1rem;
        }
    }
    .done {
        text-decoration: line-through;
    }
</style>
