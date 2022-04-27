<template>
  <Page class="page">
    <ActionBar title="Календарь" class="action-bar">
      <NavigationButton
        text="Назад"
        android.systemIcon="ic_menu_back"
        @tap="goBack"
      />
    </ActionBar>
    <ScrollView>
      <FlexboxLayout flexDirection="column" justifyContent="center">
        <FlexboxLayout flexDirection="row" justifyContent="center">
          <GridLayout
            columns="30, 30, 30, 30, 30, 30, 30"
            rows="30, 30, 30, 30, 30, 30, 30, 30, 30"
          >
            <Label
              text="<"
              style="padding: 10px; text-align: center"
              row="0"
              col="0"
              @tap="decrementYear"
            />
            <Label
              :text="year"
              style="padding: 10px; text-align: center"
              colSpan="5"
              row="0"
              col="1"
            />
            <Label
              text=">"
              style="padding: 10px; text-align: center"
              row="0"
              col="6"
              @tap="incrementYear"
            />

            <Label
              text="<"
              style="padding: 10px; text-align: center"
              row="1"
              col="0"
              @tap="decrementMonth"
            />
            <Label
              :text="getMonthText"
              style="padding: 10px; text-align: center"
              colSpan="5"
              row="1"
              col="1"
            />
            <Label
              text=">"
              style="padding: 10px; text-align: center"
              row="1"
              col="6"
              @tap="incrementMonth"
            />

            <Label
              text="Пн"
              style="padding: 10px; text-align: center"
              row="2"
              col="0"
            />
            <Label
              text="Вт"
              style="padding: 10px; text-align: center"
              row="2"
              col="1"
            />
            <Label
              text="Ср"
              style="padding: 10px; text-align: center"
              row="2"
              col="2"
            />
            <Label
              text="Чт"
              style="padding: 10px; text-align: center"
              row="2"
              col="3"
            />
            <Label
              text="Пт"
              style="padding: 10px; text-align: center"
              row="2"
              col="4"
            />
            <Label
              text="Сб"
              style="padding: 10px; text-align: center"
              row="2"
              col="5"
            />
            <Label
              text="Вс"
              style="padding: 10px; text-align: center"
              row="2"
              col="6"
            />

            <template v-for="(row, index) in 7">
              <Label
                v-for="day in 7"
                :key="day + row + index"
                :text="getDay(row - 1, day - 1)"
                :row="row + 2"
                :col="day - 1"
                style="padding: 10px; text-align: center"
                :style="[
                  today == `${getDay(row - 1, day - 1)}/${month}/${year}`
                    ? { backgroundColor: '#0178D5' }
                    : { backgroundColor: 'rgba(0, 0, 0, 0)' },
                  month == getMonth(row - 1, day - 1)
                    ? { color: '#fff' }
                    : { color: '#5c5c5c' },
                ]"
              />
            </template>
          </GridLayout>
        </FlexboxLayout>
      </FlexboxLayout>
    </ScrollView>
  </Page>
</template>

<script>
import Home from "./Home.vue";

export default {
  name: "Converter",
  methods: {
    getDay(row, col) {
      let a = undefined;
      if (row == 0) {
        a = [
          this.daysArray[0],
          this.daysArray[1],
          this.daysArray[2],
          this.daysArray[3],
          this.daysArray[4],
          this.daysArray[5],
          this.daysArray[6],
        ];
        return String(a[col]).split("/")[0];
      }
      if (row == 1) {
        a = [
          this.daysArray[7],
          this.daysArray[8],
          this.daysArray[9],
          this.daysArray[10],
          this.daysArray[11],
          this.daysArray[12],
          this.daysArray[13],
        ];
        return String(a[col]).split("/")[0];
      }
      if (row == 2) {
        a = [
          this.daysArray[14],
          this.daysArray[15],
          this.daysArray[16],
          this.daysArray[17],
          this.daysArray[18],
          this.daysArray[19],
          this.daysArray[20],
        ];
        return String(a[col]).split("/")[0];
      }
      if (row == 3) {
        a = [
          this.daysArray[21],
          this.daysArray[22],
          this.daysArray[23],
          this.daysArray[24],
          this.daysArray[25],
          this.daysArray[26],
          this.daysArray[27],
        ];
        return String(a[col]).split("/")[0];
      }
      if (row == 4) {
        a = [
          this.daysArray[28],
          this.daysArray[29],
          this.daysArray[30],
          this.daysArray[31],
          this.daysArray[32],
          this.daysArray[33],
          this.daysArray[34],
        ];
        return String(a[col]).split("/")[0];
      }
      if (row == 6) {
        a = [
          this.daysArray[35],
          this.daysArray[36],
          this.daysArray[37],
          this.daysArray[38],
          this.daysArray[39],
          this.daysArray[40],
          this.daysArray[41],
        ];
        return String(a[col]).split("/")[0];
      }
    },
    getMonth(row, col) {
      let a = undefined;
      if (row == 0) {
        a = [
          this.daysArray[0],
          this.daysArray[1],
          this.daysArray[2],
          this.daysArray[3],
          this.daysArray[4],
          this.daysArray[5],
          this.daysArray[6],
        ];
        return String(a[col]).split("/")[1];
      }
      if (row == 1) {
        a = [
          this.daysArray[7],
          this.daysArray[8],
          this.daysArray[9],
          this.daysArray[10],
          this.daysArray[11],
          this.daysArray[12],
          this.daysArray[13],
        ];
        return String(a[col]).split("/")[1];
      }
      if (row == 2) {
        a = [
          this.daysArray[14],
          this.daysArray[15],
          this.daysArray[16],
          this.daysArray[17],
          this.daysArray[18],
          this.daysArray[19],
          this.daysArray[20],
        ];
        return String(a[col]).split("/")[1];
      }
      if (row == 3) {
        a = [
          this.daysArray[21],
          this.daysArray[22],
          this.daysArray[23],
          this.daysArray[24],
          this.daysArray[25],
          this.daysArray[26],
          this.daysArray[27],
        ];
        return String(a[col]).split("/")[1];
      }
      if (row == 4) {
        a = [
          this.daysArray[28],
          this.daysArray[29],
          this.daysArray[30],
          this.daysArray[31],
          this.daysArray[32],
          this.daysArray[33],
          this.daysArray[34],
        ];
        return String(a[col]).split("/")[1];
      }
      if (row == 6) {
        a = [
          this.daysArray[35],
          this.daysArray[36],
          this.daysArray[37],
          this.daysArray[38],
          this.daysArray[39],
          this.daysArray[40],
          this.daysArray[41],
        ];
        return String(a[col]).split("/")[1];
      }
    },
    incrementMonth() {
      this.month++;
      if (this.month > 11) {
        this.month = -1;
        this.month++;
        this.year++;
      }
      this.selectedDay = 1;
    },
    decrementMonth() {
      this.month--;
      if (this.month < 0) {
        this.month = 12;
        this.month--;
        this.year--;
      }
      this.selectedDay = 1;
    },
    incrementYear() {
      this.year++;
    },
    decrementYear() {
      this.year--;
    },
    calcCalendar() {
      this.daysArray = [];
      let daysOfBeforeMonth =
        new Date(`${this.year}/${this.month}/01`).getDay() - 1;
      if (daysOfBeforeMonth == -1) {
        daysOfBeforeMonth = 6;
      }
      const daysInBeforeMonth = new Date(
        this.year,
        this.month - 1,
        0
      ).getDate();
      for (
        let index = daysInBeforeMonth - daysOfBeforeMonth + 1;
        index <= daysInBeforeMonth;
        index++
      ) {
        this.daysArray.push(`${index}/${this.month - 1}`);
      }

      const daysInCurrentMonth = new Date(this.year, this.month, 0).getDate();
      for (let index = 1; index <= daysInCurrentMonth; index++) {
        this.daysArray.push(`${index}/${this.month}`);
      }

      const other = 42 - this.daysArray.length;
      for (let index = 1; index <= other; index++) {
        this.daysArray.push(`${index}/${this.month + 1}`);
      }
    },

    goBack() {
      this.$navigateTo(Home);
    },
  },
  data() {
    return {
      year: new Date().getFullYear(),
      day: new Date().getDate(),
      month: new Date().getMonth() + 1,
      daysArray: [],
      today: `${new Date().getDate()}/${
        new Date().getMonth() + 1
      }/${new Date().getFullYear()}`,
    };
  },
  watch: {
    year() {
      this.calcCalendar();
    },
    month() {
      this.calcCalendar();
    },
  },
  computed: {
    getMonthText() {
      if (this.month == 1) return "Январь";
      if (this.month == 2) return "Февраль";
      if (this.month == 3) return "Март";
      if (this.month == 4) return "Апрель";
      if (this.month == 5) return "Май";
      if (this.month == 6) return "Июнь";
      if (this.month == 7) return "Июль";
      if (this.month == 8) return "Август";
      if (this.month == 9) return "Сентябрь";
      if (this.month == 10) return "Октябрь";
      if (this.month == 11) return "Ноябрь";
      if (this.month == 12) return "Декабрь";
    },
  },
  mounted() {
    const daysOfBeforeMonth =
      new Date(
        `${new Date().getFullYear()}/${new Date().getMonth() + 1}/01`
      ).getDay() - 1;
    const daysInBeforeMonth = new Date(
      new Date().getFullYear(),
      new Date().getMonth(),
      0
    ).getDate();
    for (
      let index = daysInBeforeMonth - daysOfBeforeMonth + 1;
      index <= daysInBeforeMonth;
      index++
    ) {
      this.daysArray.push(`${index}/${new Date().getMonth()}`);
    }

    const daysInCurrentMonth = new Date(
      new Date().getFullYear(),
      new Date().getMonth() + 1,
      0
    ).getDate();
    for (let index = 1; index <= daysInCurrentMonth; index++) {
      this.daysArray.push(`${index}/${new Date().getMonth() + 1}`);
    }

    const other = 42 - this.daysArray.length;
    for (let index = 1; index <= other; index++) {
      this.daysArray.push(`${index}/${new Date().getMonth() + 2}`);
      this.daysArray.push(index);
    }
  },
};
</script>

<style></style>
