<template>
  <form class="form" @submit.prevent="handleSubmit">
    <CustomSelect :items="cities" @selected:item.stop="handlerSelect" class="form__select" />
    <CustomInput v-model="price" :placeholderText="placeholderText" />
    <SubmitButton class="form__submit" :buttonName="'Submit Form'" type="submit" />
  </form>
</template>

<script>
import CustomSelect from "../shared/CustomSelect.vue";
import CustomInput from "../CustomInput.vue";
import SubmitButton from "../shared/SubmitButton.vue";

export default {
  name: "ApartmentFiltredForm",
  components: {
    CustomSelect,
    CustomInput,
    SubmitButton,
  },
  computed: {
     cities() {
         return [{value: "", lable: 'город', selected: true},"Kiev", "Odesa", "Dnipro", "Lviv"]
     }
  },
  data() {
    return {
      price: 0,
      city: "",
      
      placeholderText: 'Price of ...'
    };
  },
    methods: {
    handleSubmit() {
      this.$emit("submit:form", {city: this.city, price: this.price})
    },
    handlerSelect(value) {
      this.city = value;
    }
  },
};
</script>

<style lang="scss" scoped>
.form {
  display: flex;
  padding: 25px;

  &__select {
    margin-right: 30px;
  }

  &__submit {
    margin: 0 30px;
  }
}
</style>
