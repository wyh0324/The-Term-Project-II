<template>
  <div class="home-page">
    <h1 class="page-title">Olympic Medal Table</h1>

    <!-- Input Section for Number of Countries -->
    <div class="input-section">
      <label for="numCountries" class="input-label">Enter number of countries: </label>
      <input 
        v-model="numCountries" 
        type="number" 
        min="1" 
        @input="loadCountries" 
        class="input-number" 
      />
    </div>

    <!-- Countries List -->
    <div v-if="countries.length > 0" class="countries-list">
      <ul>
        <li v-for="country in countries" :key="country.id" class="country-item">
          <router-link :to="'/country/' + country.id" class="country-link">
            {{ country.name }}
          </router-link>
          - Gold: {{ country.gold }} | Silver: {{ country.silver }} | Bronze: {{ country.bronze }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numCountries: 5,
      countries: [],
    };
  },
  methods: {
    loadCountries() {
      // Mock data based on the number of countries
      this.countries = Array.from({ length: this.numCountries }, (_, i) => ({
        id: i + 1,
        name: `Country ${i + 1}`,
        gold: Math.floor(Math.random() * 10),
        silver: Math.floor(Math.random() * 10),
        bronze: Math.floor(Math.random() * 10),
      }));
    },
  },
  created() {
    this.loadCountries();
  },
};
</script>

<style scoped>
/* General Styles for the Home Page */
.home-page {
  font-family: 'Arial', sans-serif;
  max-width: 900px;
  margin: 40px auto;
  padding: 20px;
  background-color: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

.page-title {
  font-size: 2rem;
  font-weight: bold;
  color: #333;
  text-align: center;
  margin-bottom: 20px;
}

/* Input Section */
.input-section {
  margin-bottom: 20px;
  text-align: center;
}

.input-label {
  font-size: 1.1rem;
  color: #555;
  margin-right: 10px;
}

.input-number {
  padding: 10px;
  font-size: 1.1rem;
  border-radius: 5px;
  border: 1px solid #ccc;
  width: 150px;
  transition: border-color 0.3s ease;
}

.input-number:focus {
  border-color: #007bff;
  outline: none;
}

/* Countries List Styling */
.countries-list {
  margin-top: 20px;
}

.country-item {
  background-color: #fff;
  padding: 12px;
  margin: 10px 0;
  border-radius: 6px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
  font-size: 1.1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.country-link {
  font-weight: bold;
  color: #333;
  text-decoration: none;
  transition: color 0.3s ease;
}

.country-link:hover {
  color: #007bff;
}

.country-item span {
  font-style: italic;
  color: #777;
}

/* Responsive Design */
@media (max-width: 600px) {
  .home-page {
    padding: 15px;
  }
  .page-title {
    font-size: 1.8rem;
  }
  .input-number {
    width: 120px;
    font-size: 1rem;
  }
  .country-item {
    font-size: 1rem;
  }
}
</style>
