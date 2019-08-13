<template>
  <main>
    <CalendarUi :date="date" />
    <ConverterUi />
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
    increaseMonth() {
      this.dates.month = 11;
    }
  }
};
</script>
<style scoped>
main {
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
