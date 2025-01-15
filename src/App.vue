<template>
  <div class="container">
    <header class="mb-4">
      <h1>Car Rental Service</h1>
    </header>
    <div class="row">
      <div class="col-md-6 mb-4">
        <button @click="showNewCarForm = !showNewCarForm" class="btn btn-primary mb-3">
          {{ showNewCarForm ? 'Hide New Car Form' : 'Show New Car Form' }}
        </button>
        <new-car v-if="showNewCarForm" />
      </div>
      <div class="col-md-6 mb-4">
        <new-rent />
      </div>
    </div>
    <show-rents />
  </div>
</template>

<script>
import NewCar from "./components/newCar.vue";
import NewRent from "./components/newRent.vue";
import ShowRents from "./components/showRents.vue";

export default {
  components: {
    NewCar,
    NewRent,
    ShowRents,
  },
  data() {
    return {
      showNewCarForm: false,
    };
  },
};
</script>

<style>
.container {
  margin-top: 20px;
}
</style>
