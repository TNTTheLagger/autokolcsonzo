<script>
import { API_BASE_URL } from "../config/api";

export default {
  data() {
    return {
      rent: {
        email: "",
        car: null,
        startDate: "",
        endDate: "",
      },
      cars: [],
    };
  },
  async created() {
    try {
      const response = await fetch(`${API_BASE_URL}/cars`);
      if (!response.ok) throw new Error("Failed to fetch cars");
      this.cars = await response.json();
    } catch (error) {
      console.error("Error fetching cars:", error.message);
    }
  },
  methods: {
    async submitRent() {
      try {
        const response = await fetch(`${API_BASE_URL}/rents`, {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify(this.rent),
        });

        if (!response.ok) {
          throw new Error(`Failed to register rent: ${response.statusText}`);
        }

        console.log("Rent registered successfully:", await response.json());
      } catch (error) {
        console.error("Error registering rent:", error.message);
      }
    },
  },
};
</script>
