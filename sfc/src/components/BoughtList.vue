<template>
    <div>
        <h2>산 물건들</h2>
        <ul>
            <li v-for="(item, index) in filteredItems"
            :key="index">{{ item.name }}
            <button v-on:click="removeItem(item)">삭제</button>
            <button v-on:click="cancelBuy(item)">구매 취소</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: ["bought-items"],
    methods: {
        cancelBuy: function(item) {
                if (item.buy == true) {
                    item.buy = false;
            } 
        },
        removeItem: function (item) {
            console.log("삭제할 아이템:", item);
            this.$emit("remove-item", item);
            }
        },
        computed: {
            filteredItems: function() {
                return this.boughtItems.filter(item => {
                    return item.buy;
                    })
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>