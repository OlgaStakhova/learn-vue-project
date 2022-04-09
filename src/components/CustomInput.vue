<template>
    <input :placeholder="placeholderText" v-on="listeners">
</template>

<script>
export default {
    name: 'CustomInput',
    props: {
        placeholderText: {
            type: String,
            default:'default placeholder'
        }
    },
    computed: {
       listeners() {
           return {
               ...this.$listeners,
               input: event => this.$emit('input', event.target.value)
           }
       }
    }
}
</script>

<style lang="scss">

</style>