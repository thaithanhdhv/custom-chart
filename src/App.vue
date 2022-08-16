<script setup>
import moment from 'moment';
import randomColor from 'randomcolor';
const minDate = '08-10-2022';
const maxDate = '09-08-2022'
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

const date_hash = {};
let months = [];
let weeks = [];

const colors = ["#EC5785", "#00D9F5", "#7DBD51", "#DCA037", "#EC5428", "#4FA5F6", "#C14C2A", "#F19D38", "#6CD2D2", "#6631A6", "#26077C", "#7131FF", "#00ECBB", "#DB234B" ]

const getStyle = (date, dayStart, dayEnd, idx, idx1, product) => {
  const numImplemented = Math.round((product.current_progress * 1.0 / product.quantity) * getNumOfDays(dayEnd, dayStart));
  const firstImplementedDay = new Date(dayStart);
  const lastImplementedDay = moment(firstImplementedDay.setDate(firstImplementedDay.getDate() + numImplemented)).format('MM-DD-YYYY');

  var bgColor = { backgroundColor: colors[idx] }
  var borderRadius = {}
  var opacity = {}
  if (date >= dayStart && date <= dayEnd) {
    if (date == dayStart) {
      borderRadius = {borderRadius: "5px 0px 0px 5px"};
    } else if (date == dayEnd) {
      borderRadius = {borderRadius: "0px 5px 5px 0px"};
    }
    if (lastImplementedDay <= date) opacity = {opacity: 0.5};

    return {...bgColor, ...borderRadius, ...opacity};
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
  const data = date_hash[month];
  Object.values(data).forEach((value) => {
    total += value.length;
  });
  return total;
};

const getWeeksDay = (w) => {
  const data = w.split('-');
  const week = data[0];
  const month = data[1];
  const target = date_hash[month][week];
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
  uniqueMonths.forEach((item) => (date_hash[item] = {}));
  months = uniqueMonths;
  dates.forEach((item) => {
    const month = moment(item).format('MM/YYYY');
    const week = getWeekNumber(new Date(item));
    weeks.push({ week, month });
    if (!date_hash[month][week]) {
      date_hash[month][week] = [];
    }
    date_hash[month][week].push(item);
  });
};
formatData();
const uniqueWeeks = [...new Set(weeks.map((week) => week.week + '-' + week.month))];

function getDate(date) {
  return moment(date).format('DD');
}
</script>

<template>
  <div class="table" style="border: 1px solid #E4E4E4;">
    <table>
      <thead style="font-size: 125%;">
        <tr>
          <th class="th-class bb-none"></th>
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
          <th class="th-class bt-none bb-none"></th>
          <th v-for="week in uniqueWeeks" :colspan="getWeeksDay(week)" :key="`week-${week}`">
            Week {{ week.slice(0, 2) }}
          </th>
        </tr>
        <tr class="days">
          <th class="th-class bt-none" style="width: 300px;padding: 3px 14px;">
            <table style="border: none">
              <tbody>
                <tr>
                  <td style="border: none; text-align:left">PO No.</td>
                  <td style="border: none; text-align:right">Số ngày</td>
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
        v-for="(products, department_name, idx) in planedData"
        class="row"
        :key="`product-${department_name}`"
      >
        <tr class="days">
          <th class="th-class bg-department bt-none bb-none">
            <strong>
              {{ department_name }}
            </strong>
          </th>
          <td class="bg-department" :colspan="dates.length"></td>
        </tr>
        <tr v-for="(product, idx_1) in products" :key="idx_1">
          <th class="bt-none bb-none">
            <table style="border: none">
              <tbody>
                <tr>
                  <td style="border: none">{{ product.product_no }}</td>
                  <td style="border: none; text-align:right">
                    {{ getNumOfDays(product.out_date, product.in_date) }}
                  </td>
                </tr>
              </tbody>
            </table>
          </th>
          <td
            v-for="(date, idx_2) in dates"
            :key="`${date}-date`"
            :style="getStyle(date, product.in_date, product.out_date, idx, idx_2, product)"
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
  white-space: nowrap;
  margin: 0;
  border-collapse: separate;
  border-spacing: 0;
  table-layout: fixed;
  border: none;
  width: 100%;
}
table td {
  padding: 0.5rem 1rem;
}
table th {
  border-top: none;
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
table thead th {
  border: 1px solid #E4E4E4;
}
table td {
  background: #fff;
  padding: 4px 5px;
}
table tbody th {
  font-weight: 100;
  font-style: italic;
  text-align: left;
  position: relative;
  border: 1px solid #E4E4E4;
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
.th-class {
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
.bg-department {
  background-color: #F2F2F2;
}
.bt-none {
  border-top: none;
}
.bb-none {
  border-bottom: none;
}
.bl-none {
  border-left: none;
}
.br-none {
  border-right: none;
}
</style>
