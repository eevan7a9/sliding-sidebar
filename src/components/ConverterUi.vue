<template>
  <main>
    <section class="title">
      <h1>Convert Currency</h1>
      <p>{{date}}</p>
    </section>
    <section class="convert-from">
      <label for="from">From :</label>
      <select name="from_country">
        <option selected>USD</option>
        <option value="php">Php</option>
      </select>
      <input type="number" id="from_amount" placeholder="Amount" />
    </section>
    <section class="convert-to">
      <label for="to">To :</label>
      <select name="to_country" id="to_country">
        <option value="php">Php</option>
        <option value="usd">Usd</option>
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
      header: "Converter Here"
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
</style>