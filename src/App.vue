<template>
  <div id="app">
    <h1>{{ title }}</h1>
    <ButtonMy @click="increment" outlined>Click my</ButtonMy>
    
    <StarRating :rating='4'/>
    <ApartmentItem 
    :descript="apartment.descript"
    :price="apartment.price"
    :rating="apartment.rating"
    imgSrc="https://www.imgonline.com.ua/examples/bee-on-daisy.jpg"/>
    <ApartmentList :items="apartmentArr"/>
  </div>
</template>

<script>
import ButtonMy from './components/ButtonMy.vue'
import StarRating from './components/StarRating.vue'
import ApartmentItem from './components/apartment/ApartmentItem.vue'
import ApartmentList from './components/apartment/ApartmentList.vue'
import apartmentArr from './components/apartment/apartmentArr'
export default {
  name: 'App',
  components: {
    ButtonMy,
    StarRating,
    ApartmentItem,
    ApartmentList,
  },

data(){
  return {
    apartmentArr,
    amountsOfClicks: 0,
    apartment:{
      id: "rgfdjgf",
      title: "Title some",
      descript: " lorem20 ",
      price: 1254,
      rating: 3.7,
      location: {
        city: 'Korosten',
      },
      ovner: {
        name:'Elena',
        tel: '564-643-758',
      },
    }

  }
},

computed: {
  title() {
    return `Amount of click ${this.amountsOfClicks}`
  }
},
methods:{
  increment(){
    this.amountsOfClicks +=1
  }
},
}

</script>

<style>
#app {
  font-family: Montserrat, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
