<template>
    <select @input='handlerSelect' class="custom-select">
        <option v-for="item in formated" :selected='item.selected' :value="item.value" :key="item.value">
            {{item.lable}}
        </option>
    </select>
    
</template>

<script>
export default {
    name: 'CustomSelect',
    props: {
        items: {
            type: Array,
            requared: true,
        }
    },
    computed: {
       formated() {
           return this.items.map( item => {
                   if(typeof item === "object"){
                       return item
                   } else{
                       return {value: item,
                       lable: item }
                   }
               })   
       }
    },
    methods: {
        handlerSelect(e) {
            const {value} = e.target;
            this.$emit('selected:item', value)
        }
    }
}
</script>

<style lang="scss">
.custom-select {
    height: 64px;
    border: 2px solid orange;
    font-size: 18px;
    outline: none;
    padding: 8px 15px;
    cursor: pointer;
    display: inline-block;


}
</style>