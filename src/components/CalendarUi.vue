<template>
  <div class="calendar-container">
    <div class="calendar">
      <section class="calendar-head">
        <h1>Header</h1>
      </section>
      <section class="calendar-body">
        <div class="weeks">
          <div v-for="(day, index) in days" :key="index">
            <span>{{day}}</span>
          </div>
        </div>
        <div class="dates">
          <div class="date-day" v-for="(date, index) in dates" :key="index">
            <span>{{date}}</span>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  name: "CalendarUi",
  props: {
    greetings: String,
    dates: Array
  },
  data() {
    return {
      calendar_header: "2019, 08, 12",
      days: ["S", "M", "T", "W", "T", "F", "S"]
    };
  },
  methods: {
    getTotal() {}
  }
};
</script>

<style scoped>
.calendar-container {
  width: 100%;
  border: 2px solid #333;
  padding: 25px;
  height: 650px;
  background: wheat;
  display: flex;
}
.calendar {
  height: 100%;
  width: 100%;
  background: whitesmoke;
}
.calendar-head {
  height: 50px;
  width: 100%;
  border: #333 solid 1px;
}
.calendar-body {
  border: #333 solid 1px;
  width: 100%;
  height: 550px;
}
.weeks {
  height: 50px;
  border: #333 solid 1px;
  display: flex;
  flex-wrap: wrap;
}
.weeks div {
  height: 100%;
  font-size: 20px;
  font-weight: 900;
  background: cadetblue;
  flex-grow: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}
.dates {
  display: flex;
  flex-wrap: wrap;
}
.date-day {
  background: cadetblue;
  width: 14.285714285714286%;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.active {
  color: red;
}
</style>