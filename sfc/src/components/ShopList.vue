<template>
    <div>
        <h2>살 물건들</h2>
        <ul>
            <li v-for="(item, index) in filteredItems" :key="index">
                {{ item.name }}
                <button @click="buyItem(item, index)">구매</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
     props: ['shopping-items'],
     methods: {
                buyItem: function(item, index) {
                    console.log("구매할 아이템:", item);
                    item.buy = true;
                }
            },
            computed: {
                filteredItems: function() {
                    return this.shoppingItems.filter(item => {
                        return !item.buy
             })
             }
             }
}
</script>

<style lang="scss" scoped>

</style>