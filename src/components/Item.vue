<template>
    <div>
        <li>

        <span v-bind:class="{done: order.completed}">

            <input type="checkbox" v-on:change="order.completed = !order.completed"/>
            {{index + 1}}
            {{order.title}}
            <button type="submit" v-on:click="$emit('remove', order.id)">Del</button>


        </span>

        </li>
    </div>
</template>

<script>

    export default {
        props: {
            order: {
                type: Object,
                required: true
            },
            index: Number
        },
        name: "Item",

    }
</script>

<style scoped>
    li {
        border: 1px solid gray;
        display: flex;
        justify-content: space-between;
        padding: .5rem 2rem;
        margin-bottom: 1rem;
    }


    input {
        margin-right: 1rem;
    }

    .done {
        text-decoration: line-through;
    }


</style>