<template>
    <div>
      <p class='my-cl-static' @click="handlerMy"  :class="{ 'my-class':isActiv }"> {{ text }}</p>
      <p> {{ text2 }} </p>
    </div> 
</template>

<script>

export default {
    name:"TestComponent",
    data(){
        return {
            isActiv: false,
            text: 'ygygyguygygyugkkjbhikjbhkjb',
            text2: 0,
        }
    },
    methods:{
 
        handlerMy() {
           this.text2 = Math.random(0,1)
           this.isActiv = !this.isActiv;
        }

    }
}
</script>

<style scoped>

.my-cl-static{
    color:chartreuse;
}

.my-class {
    color: brown;
}

</style>
