<template>
  <div class="country-card">
    <router-link :to="'/country/' + country.id" class="card-link">
      <h3 class="country-name">{{ country.name }}</h3>
      <p class="medals-info">
        Gold: {{ country.gold }} | Silver: {{ country.silver }} | Bronze: {{ country.bronze }}
      </p>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'CountryCard',
  props: {
    country: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
/* Styling for the country card */
.country-card {
  background-color: #fff;
  padding: 20px;
  margin: 15px;
  border-radius: 8px;
  border: 1px solid #ddd;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease-in-out;
  cursor: pointer;
}

.country-card:hover {
  background-color: #f9f9f9;
  transform: translateY(-5px);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
}

/* Link styling */
.card-link {
  text-decoration: none;
  color: inherit;
}

/* Country name styling */
.country-name {
  font-size: 1.5rem;
  font-weight: bold;
  color: #333;
  margin-bottom: 8px;
  transition: color 0.3s ease;
}

.country-name:hover {
  color: #007bff;
}

/* Medal information styling */
.medals-info {
  font-size: 1.1rem;
  color: #555;
  font-style: italic;
  margin-top: 5px;
}

/* Responsive design */
@media (max-width: 600px) {
  .country-card {
    padding: 15px;
    margin: 10px;
  }
  .country-name {
    font-size: 1.3rem;
  }
  .medals-info {
    font-size: 1rem;
  }
}
</style>
