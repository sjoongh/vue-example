<template>
    <div id="app">
        <cart-header></cart-header>
        <div v-show="showAll">
            <h2>전체 목록</h2>
            <ul>
                <li v-for="(item, index) in items" v-bind:key="index">{{ item.name }}</li>
            </ul>
        </div>
        <shop-list :shopping-items="items"></shop-list>
        <cart-input @add-item="addItem"></cart-input>
        <bought-list :bought-items="items"
                    v-show="showOption"
                    @remove-item="removeItem"></bought-list>
        <cart-footer></cart-footer>
    </div>
</template>

<script>
import CartHeader from './components/CartHeader.vue';
import CartFooter from './components/CartFooter.vue';
import ShopList from './components/ShopList.vue';
import BoughtList from './components/BoughtList.vue';
import CartInput from './components/CartInput.vue';

export default {
    data: () => {
        return {
            items: [
                { name: "무", buy: false },
                { name: "배추", buy: false },
                { name: "쪽파", buy: true },
                { name: "고춧가루", buy: true }
            ],
                showAll: true,
                showOption: true
            }
        },
        methods: {
            addItem: function (item) {
            console.log("추가할 아이템:", item);
            this.items.push({
                name: item,
                buy: false
            })
        },
        removeItem: function (item) {
            var index = this.items.indexOf(item);
            if (index > -1) { 
                this.items.splice(index, 1);
                }
            }
        },
        components: {
            "cart-header": CartHeader,
            "cart-footer": CartFooter,
            "shop-list": ShopList,
            "bought-list": BoughtList,
            "cart-input": CartInput
        }
    }
</script>

<style lang="scss">
li {
    list-style: none;
    height: 30px;

    button {
        float: right;
        margin-left: 5px;
    }
}

</style>