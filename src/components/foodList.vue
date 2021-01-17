<template>
  <div class="box_list">
    <ul>
        <li 
        v-for="(food, index) in foods"
        :key="`${food}-${index}`">
            {{ food }}
        </li>
        <li
        v-for="(price, index) in prices"
        :key="`${price}-${index}`"
        >
            {{ price }}
        </li>
    </ul>
  </div>
</template>

<script>
const MAX_FOODS = 20
export default {
    props: {
        foods: {
            type: Array, default: () => []
        },
        prices: {
            type: Array, default: () => []
        }
    },
    watch: {
        foods () {
            if(this.foods.length === MAX_FOODS){
                this.$emit('stop', 'Sua cesta está cheia!!')
            }
        }
    }
}
</script>

<style>
ul{
    justify-content: space-between;
    flex-direction: column;
    display: flex;
}
</style>