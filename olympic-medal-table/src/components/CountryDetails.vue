<template>
  <div class="country-details">
    <h2 class="country-title">{{ country.name }} - Medal Details</h2>
    
    <!-- Country Info Section -->
    <div class="section country-info">
      <h3 class="section-title">Country Info</h3>
      <div class="info-item">
        <p><strong>Gold Medals:</strong> {{ country.gold }}</p>
      </div>
      <div class="info-item">
        <p><strong>Silver Medals:</strong> {{ country.silver }}</p>
      </div>
      <div class="info-item">
        <p><strong>Bronze Medals:</strong> {{ country.bronze }}</p>
      </div>
    </div>
    
    <!-- Sports Section -->
    <div class="section sports">
      <h3 class="section-title">Sports</h3>
      <ul class="sports-list">
        <li v-for="sport in country.sports" :key="sport.id" class="sport-item">
          <span class="sport-name">{{ sport.name }}</span>
          <span class="sport-medals">Medals: {{ sport.medals }}</span>
        </li>
      </ul>
    </div>

    <!-- Comments Section -->
    <div class="comments-section">
      <h3 class="section-title">Comments</h3>
      <comment-section :comments="country.comments" />
    </div>
  </div>
</template>

<script>
import CommentSection from '../components/CommentSection.vue';

export default {
  name: 'CountryDetails',
  components: {
    CommentSection,
  },
  data() {
    return {
      country: {
        id: this.$route.params.id,
        name: 'Country 1',
        gold: 5,
        silver: 3,
        bronze: 2,
        sports: [
          { id: 1, name: 'Football', medals: 2 },
          { id: 2, name: 'Swimming', medals: 3 },
        ],
        comments: [
          { id: 1, username: 'User1', avatar: 'https://randomuser.me/api/portraits/men/1.jpg', text: 'Great performance!' },
          { id: 2, username: 'User2', avatar: 'https://randomuser.me/api/portraits/women/2.jpg', text: 'Well done!' },
        ],
      },
    };
  },
};
</script>

<style scoped>
/* General Page Styles */
.country-details {
  padding: 30px;
  background-color: #f9f9f9;
  max-width: 1000px;
  margin: 20px auto;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  font-family: 'Arial', sans-serif;
}

.country-title {
  font-size: 2rem;
  font-weight: bold;
  color: #333;
  text-align: center;
  margin-bottom: 20px;
}

/* Section Titles */
.section-title {
  font-size: 1.5rem;
  color: #2d3d4f;
  margin-bottom: 10px;
  text-transform: uppercase;
  font-weight: bold;
}

/* Country Info Section */
.country-info {
  background-color: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.05);
  margin-bottom: 20px;
}

.info-item {
  margin-bottom: 10px;
}

.info-item p {
  font-size: 1.1rem;
  color: #555;
}

/* Sports Section */
.sports-list {
  list-style-type: none;
  padding-left: 0;
}

.sport-item {
  background-color: #fff;
  padding: 12px;
  margin-bottom: 10px;
  border-radius: 6px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
  font-size: 1.1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.sport-name {
  font-weight: bold;
  color: #333;
}

.sport-medals {
  font-style: italic;
  color: #777;
}

/* Comment Section */
.comments-section {
  margin-top: 30px;
}

/* Styling for Comment Section */
.comment-section {
  background-color: #fafafa;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

/* Responsive Design */
@media (max-width: 600px) {
  .country-details {
    padding: 20px;
  }

  .country-title {
    font-size: 1.8rem;
  }

  .section-title {
    font-size: 1.3rem;
  }

  .info-item p,
  .sport-item {
    font-size: 1rem;
  }
}
</style>
