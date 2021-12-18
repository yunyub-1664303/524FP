<template>
  <div id="app">
    <h1>Titanic Survival Predictor</h1>

    <p>We have analyzed the passengers' information on Titanic. Feel free to enter your information below to see if you will survive on Titanic.</p>
    <p>Please Enter number only</p>
    <div class="form">
      <label> Which class of ticket would you buy (1 for first-class): </label>
      <input type="text" v-model="pClass">
    </div>

    <div class="form">
      <label> Gender (0-female, 1-male): </label>
      <input type="text" v-model="gender">
    </div>

    <div class="form">
      <label> Age: </label>
      <input type="text" v-model="age">
    </div>

    <div class="form">
      <label> Number of Siblings onboard: </label>
      <input type="text" v-model="siblings">
    </div>

    <div class="form">
      <label> Fare (in dollars): </label>
      <input type="text" v-model="fare">
    </div>

    <div><input type="submit" @click="predict()"></div>

    <h3 v-if="res">{{ res }}</h3>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      pClass: null, 
      gender: null, 
      age: null, 
      siblings: null, 
      fare: null, 
      res: null, 
    };
  }, 
  methods: {
    predict() {
      if (!this.pClass) {
        alert('Please enter a valid class of the ticket. \nPassenger class cannot be null.');
      }
      if (!this.gender) {
        alert('Please enter a valid gender number. \nGender cannot be null.');
      }
      if (!this.age) {
        alert('Please enter a valid age. \nAge cannot be null.');
      }
      if (!this.siblings) {
        alert('Please enter the number of siblings onboard. \nNumber of siblings class cannot be null.');
      }
      if (!this.fare) {
        alert('Please enter how much you will spend on the ticket. \nFare class cannot be null.');
      }
      let a = [-2.2921, -1.4433, -1.3132, -4.4513, 2.19780];
      let b = 1;
      let prediction = a[0]*this.pClass + a[1]*this.gender + a[2]*this.age + a[3]*this.siblings + a[4]*this.fare + b;
      if (prediction > 0) {
        this.res = "Congratulations! You survived from Titanic!";
      } else {
        this.res = "Oh no! According to our predictor, you wouldn't survive from the Titanic. Luckily, you are not on it anyway!"
      }
      
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
