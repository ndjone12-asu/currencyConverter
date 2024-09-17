<script>
export default {
  name: 'Balance',
  data() {
    return {
      balance: 100,
      amount: 10,
      sliderNum: 50,
    };
  },
  emits: ['newBal', 'newAmount'],
  props: {
    currencyTypeProp: String,
    balanceProp: Number,
  },
  computed: {
    balanceString() {
      //this.balance = this.balanceProp;
      this.$emit('newBal', this.balance);
      this.$emit('newAmount', this.amount);
      return `Account Balance: ${this.balance} ` + this.currencyTypeProp;
    },
  },
  methods: {
    addBalance() {
      this.balance += this.amount;
      this.$emit('newBal', this.balance);
      //this.amount = 0;
    },
    subtractBalance() {
      if (this.amount <= this.balance) {
        this.balance -= this.amount;
        this.$emit('newBal', this.balance);
      } else {
        alert('Cannot subtract more than account balance');
      }
      //this.amount = 0;
    },
  },

  mounted() {
    console.log('Application mounted');
  },
};
</script>

<template>
  <div class="greetings">
    <h3>{{ balanceString }}</h3>
    <h3>Amount: {{ amount }} {{ currencyTypeProp }}</h3>
 
    <input type="range" v-model.number="amount" min="5" max="100" step="5" />
  
    <br />
    <button @click="addBalance">Add</button>
    <button @click="subtractBalance">Subtract</button>
    <br />
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: left;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}

input[type="range"] {
  width: 200px;
}
</style>
