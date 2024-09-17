<script>
import Balance from './components/Balance.vue';
import HelloWorld from './components/HelloWorld.vue';
import Currency from './components/Currency.vue';

export default {
  data() {
    return {
      fname: 'Nicholas',
      bal: 100,
      currencyType: '',
      amount: 5,
    };
  },
  components: {
    Balance,
    HelloWorld,
    Currency,
  },
  props: {
    currencyTypeProp: String,
    balanceProp: Number,
    amountProp: Number,
  },
};
</script>

<template>
  <header>
    <div class="wrapper">
      <!-- <input v-model="fname" /> -->
      <HelloWorld :name="this.fname" />
      <Balance
        @new-bal="(v) => (this.bal = v)"
        @new-amount="(a) => (this.amount = a)"
        :currencyTypeProp="currencyType"
        :balance="bal"
      />
      <Currency @denom="(d) => (this.currencyType = d)" :amountProp="amount" />
      <!-- <p>{{currencyType}}</p> -->
    </div>
  </header>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
  }
}
</style>
