<template>
  <main class="container-main">
    <CalendarUi :date="date" v-on:set-date="updateDate" />
    <ConverterUi :date="date" />
  </main>
</template>

<script>
// @ is an alias to /src
import CalendarUi from "../components/CalendarUi";
import ConverterUi from "../components/ConverterUi";

export default {
  name: "home",
  components: {
    CalendarUi,
    ConverterUi
  },
  data() {
    return {
      greeting: "Hello Humans",
      date: new Date()
    };
  },
  methods: {
    updateDate(changed_date) {
      this.date = new Date(
        changed_date.year,
        changed_date.month,
        changed_date.date
      );
    }
  }
};
</script>
<style scoped>
.container-main {
  background-image: radial-gradient(
    circle 801px at 10.1% 20.1%,
    rgba(209, 234, 205, 1) 5.3%,
    rgba(159, 219, 233, 1) 90%
  );
  display: flex;
  width: 100%;
}
CalendarUi {
  width: 50%;
}
ConverterUi {
  width: 50%;
}
</style>
