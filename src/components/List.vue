<template>
    <ul>
        <Item v-for="(order, i) in orders"
              v-bind:order="order"
              v-bind:index="i"
              :key="order.id"
              v-on:remove="removeItem"/>
    </ul>
    
</template>

<script>
    import Item from "@/components/Item";
    export default {
        name: "List",
        props: ['orders'],
        components: {
            Item,
        },
        methods: {
            removeItem(id) {
                this.$emit('remove', id);
                // eslint-disable-next-line no-console
                //console.log(id);
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