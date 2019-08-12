<template>
  <main>
    <CalendarUi :greetings="greeting" />
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
      greeting: "Hello Humans"
    };
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
