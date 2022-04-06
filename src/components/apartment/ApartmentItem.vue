<template>
    <div class="apartment-item" @click="log">
       <div class="apartment-item__inner">
         <img :src="imgSrc" alt="" class="apartment-item__photo">
         <div class="apartment-item__content">
             <p class="apartment-item__description">{{descript}}</p>
             <div class="apartment-item__rating">
                 <StarRating :rating="rating"/>
             </div>
             <div class="apertment-item__price"> UAH {{price}}</div>
         </div>
       </div>
    </div>
</template>

<script>
import StarRating from '../StarRating'
export default {
    name: 'ApartmentItem',
    components: {
        StarRating
    },
    props: {
        descript: {
            type: String,
            default: ''
        },
        rating: {
            type: Number,
            default: 0
        },
        price: {
            type: Number,
            required: true
        },
        imgSrc: {
            type: String,
            default: ''
        }
    },
    methods: {
        log() {
            console.log('click')
        }
    }
}
</script>

<style lang="scss" scouped>
    .apartment-item {
        position: relative;
        max-width: 350px;
        padding: 0 20px;

        &__inner {
            position: relative;
        }

        &__content {
            position: relative;
            padding: 20px;
            opacity: 0;
            transition: opacity 0,4s;
            background: rgba (11, 21, 32, 0,7);
            min-height: 200px;
            color: #fff;
            text-align: left;
            cursor: pointer;
            z-index: 1;
        }

        &:hover {
                opacity: 1;
            }

        &__photo {
            max-width: 300px;
            height: auto;
        }
        
        &__content{
            position: absolute;
            top: 0;
            left: 0;
            bottom: 0;
            right: 0;
            padding: 30px;
        }  
        &__content:hover {
            opacity: 1;
        }  
        }
    

</style>