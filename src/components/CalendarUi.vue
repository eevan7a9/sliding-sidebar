<template>
  <div class="calendar-container">
    <div class="calendar">
      <section class="calendar-head">
        <button @click="decreaseMonth">Prev</button>
        <button @click="increaseMonth">Next</button>
      </section>
      <section class="calendar-body">
        <div class="weeks">
          <div v-for="(day, index) in days" :key="index">
            <span>{{day}}</span>
          </div>
        </div>
        <div class="dates">
          <div
            class="date-day"
            v-for="(date, index) in dates_days"
            :key="index"
            v-bind:class="{'date-today':dayToday(date)}"
          >
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
    greetings: String
  },
  data() {
    return {
      calendar_header: "2019, 08, 12",
      days: ["S", "M", "T", "W", "T", "F", "S"],
      dates_days: [],
      dates: {
        year: new Date().getFullYear(),
        month: new Date().getMonth(),
        date: new Date().getDate()
      },
      today: new Date().getDate()
    };
  },
  methods: {
    dayToday(date) {
      return new Date().getDate() == date;
    },
    getLastDate(year, month) {
      return new Date(year, month + 1, 0).getDate();
    },
    getFirstDay(year, month) {
      return new Date(year, month, 1).getDay();
    },
    initCalendar() {
      const first_day = this.getFirstDay(this.dates.year, this.dates.month);
      const date_end = this.getLastDate(this.dates.year, this.dates.month);
      let date_start = 1;
      const limit = 43;
      for (let i = 1; i < limit; i++) {
        if (i <= first_day) {
          this.dates_days.push(" ");
        } else if (date_end < date_start) {
          this.dates_days.push(" ");
        } else {
          this.dates_days.push(`${date_start}`);
          date_start++;
        }
      }
    },
    increaseMonth() {
      this.dates.month += 1;
      if (this.dates.month > 11) {
        this.dates.month = 0;
      }
      this.dates_days = [];
      this.initCalendar();
      console.log(this.dates.month);
    },
    decreaseMonth() {
      this.dates.month -= 1;
      if (this.dates.month < 0) {
        this.dates.month = 12;
      }
      this.dates_days = [];
      this.initCalendar();
      console.log(this.dates.month);
    }
  },
  mounted() {
    this.initCalendar();
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
  width: 14.285714285714286%;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}
.date-today {
  background: rgb(221, 196, 196);
  border-radius: 100%;
}
.active {
  color: red;
}
</style>