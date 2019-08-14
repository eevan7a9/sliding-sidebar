<template>
  <main>
    <section class="title">
      <h1>Currency Exchange</h1>
      <p>With this free application you can compare your currency with other currencies</p>
    </section>
    <section class="convert-from">
      <label for="from">From :</label>
      <select v-model="convert_from">
        <option selected>USD</option>
        <option v-for="(currency, index) in currencies" :key="index">{{currency}}</option>
      </select>
      <input
        type="number"
        v-model="amount"
        placeholder="Amount"
        v-bind:class="{error:amountCheck(amount)}"
      />
    </section>
    <section class="convert-to">
      <label for="to">To :</label>
      <select v-model="convert_to">
        <option selected>PHP</option>
        <option v-for="(currency, index) in currencies" :key="index">{{currency}}</option>
      </select>
      <input type="text" id="to_amount" readonly placeholder="Result" v-model="result" />
    </section>
    <section class="convert-submit">
      <button @click="getResult" :disabled="amountCheck(amount)">Convert</button>
    </section>
  </main>
</template>

<script>
export default {
  name: "ConverterUi",
  props: {
    date: Date
  },
  data() {
    return {
      header: "Converter Here",
      convert_from: "USD",
      convert_to: "PHP",
      amount: 1,
      result: null,
      currencies: [
        "USD",
        "EUR",
        "AUD",
        "BRL",
        "BGN",
        "CAD",
        "CHF",
        "CNY",
        "CZK",
        "DKK",
        "GBP",
        "HRK",
        "HKD",
        "IDR",
        "ILS",
        "INR",
        "ISK",
        "JPY",
        "KRW",
        "MXN",
        "MYR",
        "MXV",
        "NOK",
        "NZD",
        "PLN",
        "PHP",
        "RON",
        "RUB",
        "SEK",
        "SGD",
        "THB",
        "ZAR"
      ]
    };
  },
  methods: {
    getResult() {
      const year = this.date.getFullYear();
      const month = this.date.getMonth() + 1;
      const date = this.date.getDate();
      fetch(
        `https://api.ratesapi.io/api/${year}-${month}-${date}?base=${this.convert_from}&symbols=${this.convert_to}`
      )
        .then(response => response.json())
        .then(data => {
          const currency_rate = Object.values(data.rates)[0];
          this.result = this.amount * currency_rate.toFixed(2);
        });
    },
    amountCheck(amount) {
      return amount != parseInt(amount) || amount < 1;
    }
  }
  // https://api.ratesapi.io/api/2019-07-12?base=USD&symbols=PHP
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Indie+Flower&display=swap");
main {
  width: 100%;
  padding: 10px;
  height: 600px;
  display: flex;
  flex-direction: column;
}
section {
  height: 25%;
  display: flex;
  justify-content: center;
  align-items: center;
}
select,
button {
  background-image: radial-gradient(
    circle 328px at 2.9% 15%,
    rgba(191, 224, 251, 1) 0%,
    rgba(232, 233, 251, 1) 25.8%,
    rgba(252, 239, 250, 1) 50.8%,
    rgba(234, 251, 251, 1) 77.6%,
    rgba(240, 251, 244, 1) 100.7%
  );
  border: white solid 1px;
  padding: 0 20px;
  cursor: pointer;
}
button:disabled,
input:read-only {
  cursor: not-allowed;
}
section select,
section input,
section button {
  height: 60px;
  font-size: 20px;
  text-align: center;
}
section input {
  width: 200px;
}
section label {
  font-size: 30px;
  width: 100px;
  text-align: right;
  margin-right: 10px;
}
.title {
  display: flex;
  flex-direction: column;
}
.title p {
  padding: 20px 0;
  font-family: "Indie Flower", cursive;
  font-size: 18px;
  font-weight: 600;
}
.error {
  border: #fb3d3d solid 2px;
  box-shadow: 0px 0px 4px 0.5px #f48080;
}
.btn-disable {
}
</style>