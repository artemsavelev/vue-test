<template>
    <div>
        <h2>Orders</h2>
        <router-link to="/">Home</router-link>

        <Add v-on:add="addOrder"/>

        <Loader v-if="loading"/>
        <List v-else-if="orders.length"
              v-bind:orders="orders"
              v-on:remove="removeItem"/>

        <p v-else>No orders</p>

    </div>
</template>

<script>
    import List from '@/components/List'
    import Add from '@/components/Add'
    import Loader from '@/components/Loader'

    export default {
        name: 'Orders',
        data() {
            return {
                orders: [],
                loading: true
            }
        },

        mounted() {

            fetch('https://jsonplaceholder.typicode.com/todos')
                .then(response => response.json())
                .then(json => {
                        this.orders = json;
                        this.loading = false
                })
        },

        components: {

            List, Add, Loader

        },
        methods: {
            removeItem(id) {
                this.orders = this.orders.filter(o => o.id !== id)

            },
            addOrder(item) {
                this.orders.push(item)
            }
        }
    }
</script>

<style scoped>

</style>