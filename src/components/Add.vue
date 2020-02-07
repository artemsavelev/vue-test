<template>

    <form v-on:submit.prevent="onSubmit">
        <input type="text" v-model="title"/>

        <button type="submit">Add</button>
    </form>

</template>

<script>
    export default {
        name: "Add",
        data() {
            return {
                title: ''
            }
        },
        methods: {
            onSubmit(){
                // eslint-disable-next-line no-console
                //console.log('test', this.title)

                if (this.title.trim()) {
                    const newOrder = {

                        id: Date.now(),
                        title: this.title,
                        completed: false
                    }

                    this.$emit('add', newOrder)
                    this.title = ''
                }
            }
        }
    }
</script>

<style scoped>
    form {
        display: flex;
        margin-bottom: 1rem;
    }
    input {
        width: 400px;
    }

</style>