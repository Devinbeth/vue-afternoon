<template>
  <div class="hello">
    <nav class='navbar' >
   <input placeholder="Location"
    v-on:keydown.enter="updateLocation"/>
    </nav>
    <p>{{ location }}</p>
    <iframe
      width="600"
      height="450"
      frameborder="0" style="border:0"
      :src="formattedLocation" allowfullscreen>
    </iframe>
    <div>
      <h2>Shapes</h2>
      <div class="shape" :class="{ diff: clicked }" @click="changeClick"></div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Location",
  props: {},
  data() {
    return {
      location: "",
      formattedLocation: "",
      click: false
    };
  },
  methods: {
    updateLocation: function(event) {
      this.location = event.target.value;
      this.createLocation()
    },
    createLocation: function() {
      let newStr = this.location.replace(/ /g, '');
      this.formattedLocation = `https://www.google.com/maps/embed/v1/place?key=AIzaSyDPOxgpLyUmh5ylWGSvrWLloRxmzqPUvv8&q=${newStr}`;
    },
    changeClick: function() {
      this.changeClick = !this.changeClick;
    }
  }
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.navbar {
  background: #42b983;
  width: 100%;
  height: 50px;
  justify-content: center;
  align-content: center;
  position: fixed;
  top: 0;
  left: 0;
}
input {
  padding: 10px;
  margin-top: 5px;
}
.shape {
  height: 50px;
  width: 50px;
  background: blue;
}
.diff {
  background: red;
}
</style>
