<template>
  <div class="new-car-form">
    <h2>Register a New Car</h2>
    <form @submit.prevent="submitCar">
      <div class="form-group">
        <label for="model">Model</label>
        <input type="text" id="model" v-model="car.model" class="form-control" required />
      </div>
      <div class="form-group">
        <label for="deposit">Deposit</label>
        <input type="number" id="deposit" v-model="car.deposit" class="form-control" required />
      </div>
      <div class="form-group">
        <label for="perKmRate">Per-Kilometer Rate</label>
        <input type="number" id="perKmRate" v-model="car.perKmRate" class="form-control" required />
      </div>
      <div class="form-group">
        <label for="dailyRate">Daily Rate</label>
        <input type="number" id="dailyRate" v-model="car.dailyRate" class="form-control" required />
      </div>
      <div class="form-group">
        <label for="description">Description</label>
        <textarea id="description" v-model="car.description" class="form-control" required></textarea>
      </div>
      <button type="submit" class="btn btn-primary">Register Car</button>
    </form>
  </div>
</template>

<script>
import { API_BASE_URL } from "../config/api";

export default {
  data() {
    return {
      car: {
        model: "",
        deposit: null,
        perKmRate: null,
        dailyRate: null,
        description: "",
      },
    };
  },
  methods: {
    async submitCar() {
      try {
        const response = await fetch(`${API_BASE_URL}/cars`, {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify(this.car),
        });

        if (!response.ok) {
          throw new Error(`Failed to register car: ${response.statusText}`);
        }

        console.log("Car registered successfully:", await response.json());
      } catch (error) {
        console.error("Error registering car:", error.message);
      }
    },
  },
};
</script>
