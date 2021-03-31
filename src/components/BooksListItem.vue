<template>
    <li>
        <span v-bind:class="{done: book.completed}">
            <input type="checkbox" 
            v-on:change="book.completed = !book.completed">
            {{book.title}}
            {{book.author}}
        </span>
        <button 
        v-on:click="$emit('remove-book', book.id)"
        >Delete</button>
    </li>
</template>

<script>
export default {
    props: {
        book: {
            type: Object,
            required: true
        }
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
        border: 2px #aaa solid;
        border-radius: 5px;
        @include flex_space-between();
        padding: .5rem 2rem;
        margin-bottom: 1rem;
    }
    button {
        background: #ccc;
        border: 2px #aaa solid;
        border-radius: 5px;
        padding: .5rem 2rem;
        font-weight: bold;
    }
    .done {
        text-decoration: line-through;
    }
</style>