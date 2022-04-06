<template>
<div v-if="isVisible">
    <h1 v-shove='false'>Title Directive</h1>
    <ul>
        <template v-for="fruit in fruits">
        <li v-if='fruit === "apple"' :key='fruit'>{{fruit}}</li>
        </template>
    </ul>
    <ul>
        <li v-for="(car, key) in cars" :key="key"> {{ key }} </li>
    </ul>
</div>
</template>

<script>
export default {
    name: 'DirectivesTest',
    data() {
        return {
            isVisible: true,
            fruits: ['apple', 'orange', 'kiwi' ],
            cars: {
                bmw:{
                    color:'red',
                },
                audi:{
                    color:'blue',
                }
            }
        }
    }

    
}
</script>

<style lang="scss" scoup >

</style>