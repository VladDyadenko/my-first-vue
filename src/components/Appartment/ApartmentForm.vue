<template>
  <ContainerMain>
    <form class="form" @submit.prevent="submitData">
      <div class="select">
        <select class="custom-select" v-model="city">
          <option value="" selected>Місто</option>
          <option
            class="custom-option"
            v-for="item in uniqueCity"
            :value="item"
            :key="item"
          >
            {{ item }}
          </option>
        </select>
      </div>
      <CustomInput v-model="price" />
      <ButtonMain type="submit" class="form__submit">Підбір житла</ButtonMain>
    </form>
  </ContainerMain>
</template>

<script>
import CustomInput from "../shared/CostomInput.vue";
import ButtonMain from "../ButtonMain.vue";
import ContainerMain from "../shared/ContainerMain.vue";
import apartments from "./appartments";

export default {
  name: "ApartmentForm",
  components: {
    CustomInput,
    ButtonMain,
    ContainerMain,
  },

  data() {
    return {
      price: "",
      city: "",
      apartments,
    };
  },
  methods: {
    submitData() {
      this.$emit("submit", {
        price: this.price,
        city: this.city,
      });
    },
  },
  computed: {
    uniqueCity() {
      const uniqueCity = [
        ...new Set(this.apartments.map((item) => item.location.city)),
      ];
      return uniqueCity.sort();
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../../assets/scss/variables";
.form {
  display: flex;
  margin-bottom: 39px;

  &__select {
    margin-right: 30px;
  }
  &__submit {
    margin-left: auto;
  }
}
.custom-select {
  min-height: 44px;
  min-width: 220px;
  border: 2px solid $main-color;
  background: #fff;
  font-size: 18px;
  outline: none;
  line-height: inherit;
  padding: 8px 15px;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}
.custom-select::-ms-expand {
  display: none;
}
.custom-option {
  width: 140px;
  color: $main-text-color;
  font-family: Montserrat;
  font-size: 18px;
  font-weight: 400;
  line-height: normal;
}
.select {
  height: 44px;
  width: 220px;
  overflow: hidden;
  position: relative;
  margin-right: 30px;
}
.select:after {
  content: "▼ ";
  padding: 17px 8px;
  position: absolute;
  right: 0;
  top: 0;
  z-index: 1;
  text-align: center;
  width: 20%;
  height: 100%;
  pointer-events: none;
}
</style>
