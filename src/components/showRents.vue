<script>
import { API_BASE_URL } from "../config/api";

export default {
  data() {
    return {
      rents: [],
    };
  },
  async created() {
    try {
      const response = await fetch(`${API_BASE_URL}/rents`);
      if (!response.ok) throw new Error("Failed to fetch rents");
      this.rents = await response.json();
    } catch (error) {
      console.error("Error fetching rents:", error.message);
    }
  },
};
</script>
