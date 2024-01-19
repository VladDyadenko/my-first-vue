<template>
  <div>
    <ApartmentForm @submit="filter" />
    <ApartmentsList :items="filteredApartments">
      <template v-slot:title>
        <h1 class="title-main">Подборка согласно выбора</h1>
      </template>
      <template v-slot:apartment="{ apartment }">
        <ApartmentsItem
          :key="apartment.id"
          :descr="apartment.descr"
          :rating="apartment.rating"
          :price="apartment.price"
          :imgSrc="apartment.imgUrl"
      /></template>
    </ApartmentsList>
  </div>
</template>

<script>
import ApartmentsList from "./components/Appartment/ApartmentsList.vue";
import ApartmentsItem from "./components/Appartment/AppartmentsItem.vue";
import ApartmentForm from "./components/Appartment/ApartmentForm.vue";
import apartments from "./components/Appartment/appartments";
export default {
  name: "App",
  components: { ApartmentsList, ApartmentsItem, ApartmentForm },
  data() {
    return {
      text: "",
      apartments,
      filters: {
        city: "",
        price: 0,
      },
    };
  },
  computed: {
    filteredApartments() {
      const filterApart = this.filterByCityName(
        this.filterByPrice(this.apartments)
      );
      // console.log(filterApart);
      return filterApart;
    },
  },
  methods: {
    filter({ city, price }) {
      if (city !== undefined) {
        this.filters.city = city;
      }

      if (price !== undefined) {
        this.filters.price = price;
      }

      console.log("this.filters", this.filters);
    },

    filterByCityName(apartments) {
      if (!this.filters.city) return apartments;

      const cityName = this.filters.city;
      return apartments.filter((apartment) => {
        return apartment.location.city === cityName;
      });
    },

    filterByPrice(apartments) {
      if (!this.filters.price) return apartments;

      const filterPrice = this.filters.price;
      return apartments.filter((apartment) => {
        // console.log("apartment", apartment);
        return apartment.price >= filterPrice;
      });
    },
  },
  // watch: {
  //   filters: {
  //     deep: true,
  //     handler(newValue) {
  //       console.log("newValue", newValue);
  //     },
  //   },
  // },
};
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
.title-main {
  color: #000;
  font-family: Montserrat;
  font-size: 20px;
  text-align: start;
  font-weight: 700;
  line-height: normal;
  margin-bottom: 20px;
}
</style>
