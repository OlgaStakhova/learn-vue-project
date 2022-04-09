<template>
    <button v-on='$listeners' :type='type' :class="{'btn': true, 'btn--outline': outlined}">
      {{ buttonName }}   
    </button>
</template>

<script>
export default {
    name: 'SubmitButton',
    props: {
        buttonName: {
          type:String,
          default: 'Submit'
        },
        type:{
            type: String,
            default: "button"
        },
         outlined: {
            type: Boolean,
            default: false,
        },
    },
   

}
</script>

<style lang="scss" scoped>

.btn {
    display: inline-block;
    font-size: 38px;
    background-color: chocolate;
    color:#fff;
    cursor: pointer;
    min-width: 220px;
    border: 1px, solid, transparent;
    padding: 8px 15px;

    &--outline{
background: none;
border:1px solid chocolate;
color: chocolate;
    }
}

</style>