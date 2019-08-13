<template>
  <div class="calendar-container">
    <div class="calendar">
      <section class="calendar-head">
        <h2 @click="decreaseMonth">&lt;&lt;</h2>
        <h1>{{dates.year}} {{getMonthLongName()}}</h1>
        <h2 @click="increaseMonth">&gt;&gt;</h2>
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
            <span
              @click="$emit('set-date', {year:dates.year, month:dates.month, date:setNewDate(date)})"
            >{{date}}</span>
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
    date: Date
  },
  data() {
    return {
      calendar_header: "2019, 08, 12",
      days: ["S", "M", "T", "W", "T", "F", "S"],
      dates_days: [],
      dates: {
        year: this.date.getFullYear(),
        month: this.date.getMonth(),
        date: this.date.getDate()
      }
      // today: new Date().getDate()
    };
  },
  methods: {
    dayToday(date) {
      return this.dates.date == date;
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
    getMonthLongName() {
      const the_date = new Date(
        this.dates.year,
        this.dates.month,
        this.dates.date
      );
      return the_date.toLocaleString("default", { month: "long" });
    },
    increaseMonth() {
      this.dates.month += 1;
      if (this.dates.month > 11) {
        this.dates.year += 1;
        this.dates.month = 0;
      }
      this.$emit("set-date", {
        year: this.dates.year,
        month: this.dates.month,
        date: this.dates.date
      });
      this.dates_days = [];
      this.initCalendar();
      // console.log(this.dates.month);
    },
    decreaseMonth() {
      this.dates.month -= 1;
      if (this.dates.month < 0) {
        this.dates.year -= 1;
        this.dates.month = 11;
      }
      this.$emit("set-date", {
        year: this.dates.year,
        month: this.dates.month,
        date: this.dates.date
      });
      this.dates_days = [];

      this.initCalendar();
      // console.log(this.dates.month);
    },
    setNewDate(new_date) {
      this.dates_days = [];
      this.dates.date = new_date;
      this.initCalendar();
      return new_date;
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
  height: 600px;
  background-image: radial-gradient(
    circle 801px at 10.1% 20.1%,
    rgba(209, 234, 205, 1) 5.3%,
    rgba(159, 219, 233, 1) 90%
  );
  display: flex;
}
.calendar {
  width: 100%;
}
.calendar-head {
  height: 50px;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-image: radial-gradient(
    circle 801px at 10.1% 20.1%,
    rgba(209, 234, 205, 1) 5.3%,
    rgba(159, 219, 233, 1) 90%
  );
}
.calendar-head h2 {
  cursor: pointer;
  height: 100%;
  width: 100px;
  font-size: 28px;
  font-weight: 900;
  color: #333;
  display: flex;
  justify-content: center;
  align-items: center;
}
.calendar-body {
  width: 100%;
}
.weeks {
  height: 50px;
  display: flex;
  flex-wrap: wrap;
  border-left: white solid 1px;
}
.weeks div {
  height: 100%;
  font-size: 20px;
  font-weight: 900;
  flex-grow: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  border-right: white solid 1px;
}
.dates {
  display: flex;
  flex-wrap: wrap;
  padding-top: 50px;
}
.date-day {
  width: 14.285714285714286%;
  height: 50px;
  font-weight: 900;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  color: rgb(75, 75, 75);
  border: white solid 1px;
  background-image: radial-gradient(
    circle 328px at 2.9% 15%,
    rgba(191, 224, 251, 1) 0%,
    rgba(232, 233, 251, 1) 25.8%,
    rgba(252, 239, 250, 1) 50.8%,
    rgba(234, 251, 251, 1) 77.6%,
    rgba(240, 251, 244, 1) 100.7%
  );
}
.date-day span:hover {
  background: white;
  border-radius: 100%;
  width: 50px;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.date-today span {
  background: #2b2121;
  color: whitesmoke;
  border-radius: 100%;
  width: 50px;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.active {
  color: red;
}
</style>