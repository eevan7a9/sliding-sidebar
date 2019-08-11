<template>
  <div id="calendar">
    <h1>{{calendar_header}}</h1>
  </div>
</template>

<script>
export default {
  name: "CalendarUi",
  props: {
    greeting: String
  },
  components: {},
  data() {
    return {
      calendar_header: "2019, 08, 12"
    };
  }
};
</script>

<style scoped>
#calendar {
  width: 100%;
  border: 2px solid #333;
  padding: 10px;
  height: 600px;
  background: wheat;
}
</style>