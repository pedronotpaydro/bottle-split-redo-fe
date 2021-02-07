<template>
  <div id="app">
    <Nav />

    <BeerCard :currentBeers="beers" :currentEvents="events" />
  </div>
</template>
<script>
import Nav from "./components/Nav";
import BeerCard from "./components/BeerCard";
export default {
  name: "app",
  components: {
    Nav,
    BeerCard,
  },
  data: function() {
    return {
      beers: [],
      events: [],
    };
  },
  created: function() {
    this.indexBeers();
    this.indexEvents();

    console.log(this.beers);
  },

  methods: {
    indexBeers: function() {
      fetch("http://localhost:3000/api/beers", {
        method: "get",
      })
        .then((response) => {
          return response.json();
        })
        .then((jsonData) => {
          (this.beers = jsonData), console.log(this.beers);
        });
    },
    indexEvents: function() {
      fetch("http://localhost:3000/api/events", {
        method: "get",
      })
        .then((response) => {
          return response.json();
        })
        .then((jsonData) => {
          (this.events = jsonData), console.log(this.events);
        });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
