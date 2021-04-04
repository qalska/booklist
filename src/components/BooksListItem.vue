<template>
    <li>
        <div class="content" v-show="!isEditing">
            <span>
                <input type="checkbox" 
                v-on:change="book.completed = !book.completed">
                <span class="content-title">Title:</span>
                <span class="content-text" v-bind:class="{done: book.completed}">{{book.title}}</span>
                <span class="content-title">Author:</span>
                <span class="content-text" v-bind:class="{done: book.completed}">{{book.author}}</span>
            </span>
            <span>
                <button v-on:click="showForm">Edit</button>
                <button 
                v-on:click="$emit('remove-book', book.id)"
                >Delete</button>
            </span>
        </div>
        <div class="content" v-show="isEditing">
            <span>
                <label>Title:</label>
                <input type='text' v-model="book.title" >
            </span>
            <span>
                <label>Author:</label>
                <input type='text' v-model="book.author" >
            </span>
            <button v-on:click="hideForm">Close</button>
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
    .content {
        @include flex_space-between();
        &-title{
            font-size: 16px;
            font-weight: bold;
            margin-right: 5px;
        }
        &-text{
            font-size: 16px;
            margin-right: 30px;
        }
    }
    li {
        width: 75%;
        margin: 0 auto;
        border: 2px #aaa solid;
        border-radius: 5px;
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
    input {
        border: 2px #aaa solid;
        border-radius: 5px;
        padding: 5px 5px;
        text-align: center;
        font-size: 16px;
    }
    label {
        font-weight: bold;
        font-size: 16px;
        margin-right: 10px;
    }
</style>