<template>
<div class="star-rating">
    <span v-for="index in starLimit" :key="index" class="star star--outline"></span>
    <div class="star-rating__fullfilled" :style="ratingWidthStyle">
       <span v-for="index in starLimit" :key="index" class="star star--colored"></span>
    </div>
</div>
    
</template>

<script>
export default {
    name: 'StarRating',
    props: {
        rating: {
            type: Number,
            default: 0
        },
        starLimit: {
            type: Number,
            default: 5
        }
    },
    computed: {
        ratingWidth(){
            return this.rating/ this.starLimit *100 
        },
        ratingWidthStyle(){
            return  `width:${this.ratingWidth}%;`
        }
        }
    }


</script>

<style lang="scss" scoped>
.star-rating {
 position: relative;
 display:inline-flex;
  &__fullfilled {
      display:inline-flex;
      position:absolute;
      width: 0;
      height: 100%;
      top:0;
      left: 0;
      overflow: hidden;
  }
}
.star {
    display: block;
    width: 16px;
    height: 16px;
    margin: 0 5;
    flex-shrink: 0;
    
    &--colored {background-image: url('../assets/star-svgrepo-com.svg');
    background-repeat: no-repeat;
    background-size: cover;
     }

    &--outline { background-image: url('../assets/star-outline-svgrepo-com.svg');
    background-repeat: no-repeat;
    background-size: cover;
     }
}
</style>