<template>
  <div>
    <section>
      Filter
    </section>
    <section>
      <base-card>
        <div class="controls">
          <base-button mode="outline">Refresh</base-button>
          <base-button link to="register">Register as Coach</base-button>
        </div>
        <ul v-if="hasCoaches">
          <coach-item
            v-for="coach in filteredCoaches"
            :key="coach"
            :id="coach.id"
            :firstName="coach.firstName"
            :lastName="coach.lastName"
            :rate="coach.hourlyRate"
            :areas="coach.areas"
          ></coach-item>
        </ul>
        <p v-else>No coached available</p>
      </base-card>
    </section>
  </div>
</template>

<script>
import CoachItem from '../../components/coaches/CoachItem.vue';
import BaseButton from '../../ui/BaseButton.vue';

export default {
  components: { CoachItem, BaseButton },
  computed: {
    hasCoaches() {
      return this.$store.getters['coaches/hasCoaches'];
    },
    filteredCoaches() {
      return this.$store.getters['coaches/coaches'];
    }
  }
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

.controls {
  display: flex;
  justify-content: space-between;
}
</style>
