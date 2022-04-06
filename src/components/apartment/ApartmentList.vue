 <template>
     <div class="apartments-list">
        <ContainerPage>
         <ApartmentItem
         v-for="{id, descript, price, rating, img} in items"
         :key="id"
         :descript="descript"
         :price="price"
         :rating="rating"
         :imgSrc="img"
         />
        </ContainerPage>
     </div>
 </template>

 <script>
import ContainerPage from "../shared/ContainerPage.vue"
 import ApartmentItem from "./ApartmentItem.vue"
 
 export default {
     name: "ApartmentList",
     components: {
      ApartmentItem,
      ContainerPage,
      
     },
     props: {
         items: {
             type: Array,
             default: () => [],
         }
     }
 }
 </script>

 <style lang="scss">
    
 
 </style>