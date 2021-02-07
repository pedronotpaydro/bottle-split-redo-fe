<template>
  <b-container>
    <b-row>
      <ul>
        <li v-for="currentBeer in currentBeers" v-bind:key="currentBeer.id">
          {{ currentBeer.name,  }} brewed by: {{ currentBeer.brewery }}
        </li>
      </ul>
      <ul>
        <li v-for="currentEvent in currentEvents" v-bind:key="currentEvent.id">
          {{ currentEvent.event_name }} info:
          {{ currentEvent.event_description }}
        </li>
      </ul>
    </b-row>
  </b-container>
</template>
<script>
export default {
  props: {
    currentBeers: {
      type: Array,
      required: true,
    },
    currentEvents: {
      type: Array,
      required: true,
    },
  },
};
</script>
<style scoped>
.container {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
