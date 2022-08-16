<script setup>
import moment from 'moment';
import randomColor from 'randomcolor';
// const months = {
//     "8/2022": 10,
//     "9/2022": 20
// }
// const weeks= {
//     "week 1": 3,
//     "week 2": 7,
//     "week 3": 7,
//     "week 4": 7,
//     "week 3": 6
// }
const dates = [
  '08-10-2022',
  '08-11-2022',
  '08-12-2022',
  '08-13-2022',
  '08-14-2022',
  '08-15-2022',
  '08-16-2022',
  '08-17-2022',
  '08-18-2022',
  '08-19-2022',
  '08-20-2022',
  '08-21-2022',
  '08-22-2022',
  '08-23-2022',
  '08-24-2022',
  '08-25-2022',
  '08-26-2022',
  '08-27-2022',
  '08-28-2022',
  '08-29-2022',
  '08-30-2022',
  '08-31-2022',
  '09-01-2022',
  '09-02-2022',
  '09-03-2022',
  '09-04-2022',
  '09-05-2022',
  '09-06-2022',
  '09-07-2022',
  '09-08-2022',
];
const planedData = {
  'Chuyền 1': [
    {
      product_no: 'V_DB_KCS_2',
      style_code: 142,
      color_code: 176,
      quantity: 40,
      performance: 20,
      current_progress: 15,
      in_date: '08-11-2022',
      out_date: '08-23-2022',
    },
    {
      product_no: 'V_DB_KCS_3',
      style_code: 142,
      color_code: 176,
      performance: 20,
      quantity: 40,
      current_progress: 15,
      in_date: '08-24-2022',
      out_date: '08-30-2022',
    },
  ],
  'Chuyền 2': [
    {
      product_no: 'V_DB_KCS_2',
      style_code: 142,
      color_code: 176,
      quantity: 40,
      performance: 20,
      current_progress: 15,
      in_date: '08-11-2022',
      out_date: '08-23-2022',
    },
    {
      product_no: 'V_DB_KCS_3',
      style_code: 142,
      color_code: 176,
      quantity: 40,
      performance: 20,
      current_progress: 15,
      in_date: '08-24-2022',
      out_date: '08-30-2022',
    },
  ],
};

let randomColors = {};
const abc = {};
let months = [];
let weeks = [];

Object.values(planedData).forEach((item) => {
  item.forEach((i) => {
    randomColors[i.product_no] = randomColor();
  });
});

const getRandomColor = (index) => {
  const randomNumber = Math.floor(Math.random() * randomColors.length) + 1;
  return index ? randomColors[index] : randomColors[randomNumber];
};

const getStyle = (date, dayStart, dayEnd, key) => {
  const color = getRandomColor(key);
  if (date >= dayStart && date <= dayEnd) {
    return {
      backgroundColor: color,
    };
  }
  return {};
};
const getNumOfDays = (day1, day2) => {
  const date1 = new Date(day1);
  const date2 = new Date(day2);
  const difference = date1.getTime() - date2.getTime();
  const totalDay = Math.ceil(difference / (1000 * 3600 * 24));
  return totalDay;
};

const calculateMonthDays = (month) => {
  let total = 0;
  const data = abc[month];
  Object.values(data).forEach((value) => {
    total += value.length;
  });
  return total;
};

const getWeeksDay = (w) => {
  const data = w.split('-');
  const week = data[0];
  const month = data[1];
  const target = abc[month][week];
  return target.length;
};

const getWeekNumber = (d) => {
  d = new Date(Date.UTC(d.getFullYear(), d.getMonth(), d.getDate()));
  d.setUTCDate(d.getUTCDate() + 4 - (d.getUTCDay() || 7));
  const yearStart = new Date(Date.UTC(d.getUTCFullYear(), 0, 1));
  const weekNo = Math.ceil(((d - yearStart) / 86400000 + 1) / 7);
  return weekNo;
};

const formatData = () => {
  const uniqueMonths = [...new Set(dates.map((date) => moment(date).format('MM/YYYY')))];
  uniqueMonths.forEach((item) => (abc[item] = {}));
  months = uniqueMonths;
  dates.forEach((item) => {
    const month = moment(item).format('MM/YYYY');
    const week = getWeekNumber(new Date(item));
    weeks.push({ week, month });
    if (!abc[month][week]) {
      abc[month][week] = [];
    }
    abc[month][week].push(item);
  });
};
formatData();
const uniqueWeeks = [...new Set(weeks.map((week) => week.week + '-' + week.month))];

function getDate(date) {
  return moment(date).format('DD');
}
</script>

<template>
  <div class="table">
    <table>
      <thead>
        <tr>
          <th class="abc" style="border-bottom: none"></th>
          <th
            v-for="month in months"
            :colspan="calculateMonthDays(month)"
            class="month-date"
            :key="`${month}-month`"
            :style="{ width: `${calculateMonthDays(month) * 50}px` }"
          >
            {{ month }}
          </th>
        </tr>
        <tr class="weeks">
          <th class="abc" style="border-top: none; border-bottom: none"></th>
          <th v-for="week in uniqueWeeks" :colspan="getWeeksDay(week)" :key="`week-${week}`">
            Week {{ week.slice(0, 2) }}
          </th>
        </tr>
        <tr class="days">
          <th class="abc" style="border-top: none; width: 300px">
            <table style="border: none">
              <tbody>
                <tr>
                  <td style="border: none">PO No.</td>
                  <td style="border: none">Số ngày</td>
                </tr>
              </tbody>
            </table>
          </th>
          <th v-for="date in dates" :key="date">
            {{ getDate(date) }}
          </th>
        </tr>
      </thead>
      <tbody
        v-for="(products, department_name) in planedData"
        class="row"
        :key="`product-${department_name}`"
      >
        <tr class="days">
          <th class="abc">
            {{ department_name }}
          </th>
          <td colspan="30"></td>
        </tr>
        <tr v-for="(product, idx) in products" :key="idx">
          <th>
            <table style="border: none">
              <tbody>
                <tr>
                  <td style="border: none">{{ product.product_no }}</td>
                  <td style="border: none">
                    {{ getNumOfDays(product.out_date, product.in_date) }}
                  </td>
                </tr>
              </tbody>
            </table>
          </th>
          <td
            v-for="date in dates"
            :key="`${date}-date`"
            :style="getStyle(date, product.in_date, product.out_date, product.product_no)"
            :class="date >= product.in_date && date <= product.out_date ? `bg-color` : ``"
          ></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<style lang="scss">
#app {
  margin-top: 100px;
}
.chart {
  position: relative;
  width: 100%;
  height: 300px;
  max-height: 300px;
  overflow-y: scroll;
  color: black;
  margin: 0 auto;

  &--left {
    vertical-align: top;
    min-width: 200px;
    display: inline-block;
  }
  &--right {
    display: inline-block;
    max-width: calc(100% - 200px);
    overflow-x: scroll;
    &::-webkit-scrollbar {
      display: none;
    }
    &--header {
      display: flex;
    }
  }
}
.month--weeks--name,
.month--weeks--dates,
.month--name {
  padding: 5px;
  max-height: 15px;
  height: 15px;
}
.month {
  &--header {
    display: flex;
    flex-direction: column;
  }

  &--name {
    text-align: left;
  }
  &--weeks {
    display: flex;

    &--item {
      flex: 0 0 25%;
      text-align: left;
    }

    &--dates {
      width: 100%;
      display: flex;
      justify-content: space-between;
    }
  }
  &--dates {
    display: flex;

    &--item {
      min-width: 30px;
      width: 30px;
    }
  }
}
.space,
.line-desc {
  height: 25px;
}
.line-desc {
  display: flex;
  justify-content: space-between;
  padding: 0 5px;
  align-items: center;
}
.event--item,
.body-items {
  height: 30px;
  line-height: 30px;
}
.ps__rail-x {
  position: fixed;
  opacity: 1;
  left: 200px !important;
}
table {
  font-size: 125%;
  white-space: nowrap;
  margin: 0;
  border: none;
  border-collapse: separate;
  border-spacing: 0;
  table-layout: fixed;
  border: 1px solid black;
  width: 100%;
}
table td,
table th {
  border: 1px solid black;
  padding: 0.5rem 1rem;
}
table thead th {
  padding: 3px;
  position: sticky;
  top: 0px;
  z-index: 1;
  background: white;
  min-width: 50px;
}
table td {
  background: #fff;
  padding: 4px 5px;
  text-align: center;
}

table tbody th {
  font-weight: 100;
  font-style: italic;
  text-align: left;
  position: relative;
}
table thead th:first-child {
  position: sticky;
  left: 0;
  z-index: 2;
}
table tbody th {
  position: sticky;
  left: 0;
  background: white;
  z-index: 1;
}

.abc {
  width: 350px !important;
}
.table {
  max-height: 300px;
  overflow: scroll;
}
.month-date {
  width: 1000px;
  min-width: 1000px;
}
tr.weeks th {
  top: 31px;
}
tr.days th {
  top: 62px;
}

.bg-color {
  background-color: red;
}
</style>
