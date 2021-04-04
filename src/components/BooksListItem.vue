<template>
    <li>
        <div v-show="!isEditing">
            <span v-bind:class="{done: book.completed}">
                <input type="checkbox" 
                v-on:change="book.completed = !book.completed">
                {{book.title}}
                {{book.author}}
            </span>
            <span>
                <button v-on:click="showForm">Edit</button>
                <button 
                v-on:click="$emit('remove-book', book.id)"
                >Delete</button>
            </span>
        </div>
        <div v-show="isEditing">
            <label>Title</label>
            <input type='text' v-model="book.title" >
            <label>Author</label>
            <input type='text' v-model="book.author" >
            <button class='ui basic blue button' v-on:click="hideForm">Close</button>
        </div>
    </li>
</template>

<script>
export default {
    props: {
        book: {
            type: Object,
            required: true
        }
    },
    data() {
        return {
        isEditing: false,
        }
    },
    methods: {
        showForm() {
            this.isEditing = true;
        },
        hideForm() {
            this.isEditing = false;
        },
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
        margin-right: 30px;
    }
    .done {
        text-decoration: line-through;
    }
</style>