<template>
  <div id="app">
    <h1>{{ text }}</h1>
    <h2>{{ title }}</h2>
    <h2>{{ text2 }}</h2>
     <h2>{{ sumSome }}</h2>
    <ButtonMy @click="increment" outlined>Click my</ButtonMy>
    <input type="text" v-model="text2"/>
    <ContainerPage>
    <ApartmentFiltredForm @submit:form="formDataHandler"/>
    </ContainerPage>
       
    <StarRating :rating='4'/>
    <ApartmentItem 
    :descript="apartment.descript"
    :price="apartment.price"
    :rating="apartment.rating"
    imgSrc="https://www.imgonline.com.ua/examples/bee-on-daisy.jpg"/>
    <p v-if="!filteredApartmens.length" > Not items, go serch...</p>  
    <ApartmentList v-else :items="filteredApartmens"/>
  </div>
</template>

<script>
import ButtonMy from './components/ButtonMy.vue'
import StarRating from './components/StarRating.vue'
import ApartmentItem from './components/apartment/ApartmentItem.vue'
import ApartmentList from './components/apartment/ApartmentList.vue'
import apartmentArr from './components/apartment/apartmentArr'
import ContainerPage from './components/shared/ContainerPage.vue'

import ApartmentFiltredForm from './components/apartment/ApartmentFiltredForm.vue'
export default {
  name: 'App',
  components: {
    ButtonMy,
    StarRating,
    ApartmentItem,
    ApartmentList,
    ApartmentFiltredForm,
    ContainerPage,
  },

data(){
  return {
    apartmentArr,
    amountsOfClicks: 0,
    text: "",
    text2: "",

    fiters: {
      city: '',
      price: 0,
    },

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
  },

  sumSome(){
    return this.amountsOfClicks + 100;
  },

  filteredApartmens() {
    return this.filterByCityName(this.filterByPrice(this.apartmentArr))
  }
},
methods:{
  increment(){
    this.amountsOfClicks +=1
  },

  logger(value){
    console.log(value)
  },

  formDataHandler(data) {
    console.log(data)
    this.fiters.city = data.city,
    this.fiters.price = data.price
  },

 filterByCityName(apartmentArr) {
   if(!this.fiters.city) {
     return apartmentArr;
   }
    
   return apartmentArr.filter(apartment => {
     return apartment.location.city === this.fiters.city
   })
 },

 filterByPrice(apartmentArr) {
   if(!this.fiters.price) return apartmentArr
   return apartmentArr.filter( apartment => {
     return apartment.price >= this.fiters.price
   }
   )
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
