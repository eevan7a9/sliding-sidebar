<template>
  <main>
    <section class="title">
      <h1>Convert Currency</h1>
      <p>{{date}}</p>
    </section>
    <section class="convert-from">
      <label for="from">From :</label>
      <select v-model="convert_from">
        <option selected>USD</option>
        <option v-for="(currency, index) in currencies" :key="index">{{currency}}</option>
      </select>
      <input type="number" id="from_amount" placeholder="Amount" />
    </section>
    <section class="convert-to">
      <label for="to">To :</label>
      <select v-model="convert_to">
        <option selected>PHP</option>
        <option v-for="(currency, index) in currencies" :key="index">{{currency}}</option>
      </select>
      <input type="text" id="to_amount" readonly placeholder="Result" />
    </section>
    <section class="convert-submit">
      <button @click="showSomething">Convert</button>
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
    showSomething() {
      console.log("hello World");
    }
  }
  // https://api.ratesapi.io/api/2019-07-12?base=USD&symbols=PHP
};
</script>

<style scoped>
main {
  width: 100%;
  border: 1px solid rgb(122, 121, 121);
  padding: 10px;
  height: 600px;
  background: whitesmoke;
  display: flex;
  flex-direction: column;
}
section {
  height: 25%;
  display: flex;
  justify-content: center;
  align-items: center;
}

section select,
section input,
section button {
  height: 60px;
  font-size: 20px;
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
}
</style>