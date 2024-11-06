<template>
  <div id="main">
    <h1>Ticket booking system for cinemas</h1>
    <form action="">
      <div class="form-group">
        <label for="name">Name: </label>
        <input type="text" id="name" name="name" v-model="name" />
      </div>
      <div class="form-group">
        <label for="age">Age: </label>
        <input type="text" id="age" name="name" v-model="age" />
      </div>
      <div class="form-group">
        <label for="date">Select a date:</label>
        <input class="date" type="date" id="date" name="date" @change="getDayOfWeek()" />
      </div>
      <div class="form-group">
        <label for="count">Tickets Count:</label>
        <input class="count" type="number" id="count" name="date" v-model="count" />
      </div>

      <button>Calculate</button>
    </form>
  </div>
  <div class="wrapper">
    <div type="text" class="display">
      <h3>-Ticket Prices for:</h3>
      <ul>
        <li>Name: {{ name }}</li>
        <li>Age: {{ age }}</li>
        <li>date: {{ day }}, {{ date }}.</li>
        <li>Count: {{ count }}</li>
        <li>Price: {{ price }}</li>
        <li>Total: {{ total }}</li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  name: 'App',
  components: {},
  data() {
    return {
      name: 'Moe',
      age: '31',
      group: '5',
      day: '',
      date: '',
      total: '',
      count: '',
      price: '',
      string: `You are building a ticket booking system for a cinema. 
      The system needs to calculate the ticket price based on the following criteria:
      Children (age 0-12): $5 per ticket
      Teenagers (age 13-17): $8 per ticket
      Adults (age 18-64): $12 per ticket
      Seniors (age 65+): $10 per ticket
      Additionally, there are some special conditions:
      If a group of 5 or more people books tickets together, they are eligible for a 10% discount on the total price.
      On weekends (Saturday and Sunday), there is a 5% surcharge on the ticket price for adults
      `,
    }
  },
  methods: {
    getDayOfWeek() {
      console.log('getDayOfWeek')
      this.date = document.getElementById('date').value

      if (this.date < new Date().toISOString().split('T')[0]) {
        alert('Please select a future date')
        return
      }
      let day = new Date(this.date).getDay()
      let days = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday']
      this.day = days[day]
      console.log(this.day)
    },
  },
}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  display: grid;
  grid-template-columns: 1fr 1fr;
}
#main {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
  min-height: 30vh;
}
h1 {
  text-align: center;
}
.date {
}
form {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 30vh;
}
.display {
  width: 100%;
  height: 100%;
  font-size: 20px;
  text-align: left;
  padding: 10px;
  border-radius: 0.3rem;
  overflow: scroll;

  /* Old digital calculator styling with green background and texture */
  background-color: #33ff33;
  background-image:
    linear-gradient(transparent 95%, rgba(0, 0, 0, 0.02) 5%),
    /* Horizontal lines */ linear-gradient(90deg, transparent 95%, rgba(0, 0, 0, 0.02) 5%); /* Vertical lines */
  background-size: 3px 3px; /* Adjust to make the texture finer or coarser */
  color: #000000;
  font-family: 'Courier New', monospace;
  letter-spacing: 2px;

  /* Optional shadow effects for realism */
  text-shadow: 0px 0px 1px #000;
  border: 2px solid #1a1a1a;
  box-shadow:
    inset 0 0 10px #0f3d0f,
    0px 2px 4px rgba(0, 0, 0, 0.2); /* Inner and outer shadows */

  /* Slight opacity for the text, mimicking the old displays */
  opacity: 0.9;
}
</style>
