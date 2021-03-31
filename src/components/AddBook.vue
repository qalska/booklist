<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title">
        <input type="text" v-model="author">
        <button type="submit">Create</button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            title: '',
            author: ''
        }
    },
    methods: {
        onSubmit() {
            if (this.title.trim()) {
                const newBook = {
                    id: Date.now(),
                    title: this.title,
                    author: this.author,
                    completed: false
                }
                this.$emit('add-book', newBook)
                this.title = ''
                this.author = ''
            }
        }
    }
}
</script>

<style scoped>
    input {
        width: 300px;
        margin-right: 30px;
    }
    button {
        background: #ccc;
        border: 2px #aaa solid;
        border-radius: 5px;
        padding: .5rem 2rem;
        font-weight: bold;
    }
</style>