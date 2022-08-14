<script setup>
import { onMounted, nextTick } from 'vue';
import PerfectScrollbar from 'perfect-scrollbar';
import '../node_modules/perfect-scrollbar/css/perfect-scrollbar.css';
onMounted(async () => {
  await nextTick();
  const ps = new PerfectScrollbar('.chart--right', {
    wheelSpeed: 2,
  })
  const elm = document.querySelector('.chart');
  const position = elm.getBoundingClientRect();
  const top = position.top;
  const target = document.querySelector('.ps__rail-x');
  if (target) {
    target.style.top = `${top + 300}px`;
  }
});

const months = {
    "8/2022": 10,
    "9/2022": 20
}
const weeks= {
    "week 1": 3,
    "week 2": 7,
    "week 3": 7,
    "week 4": 7,
    "week 5": 6
}
const dates = [
      "10-08-2022",
      "11-08-2022",
      "12-08-2022",
      "13-08-2022",
      "14-08-2022",
      "15-08-2022",
      "16-08-2022",
      "17-08-2022",
      "18-08-2022",
      "19-08-2022",
      "20-08-2022",
      "21-08-2022",
      "22-08-2022",
      "23-08-2022",
      "24-08-2022",
      "25-08-2022",
      "26-08-2022",
      "27-08-2022",
      "28-08-2022",
      "29-08-2022",
      "30-08-2022",
      "31-08-2022",
      "01-09-2022",
      "02-09-2022",
      "03-09-2022",
      "04-09-2022",
      "05-09-2022",
      "06-09-2022",
      "07-09-2022",
      "08-09-2022"
]
const planedData = {
    "Chuyền 1": [
      {
        "product_no": "V_DB_KCS_2",
        "style_code": 142,
        "color_code": 176,
        "quantity": 40,
        "performance": 20,
        "current_progress": 15,
        "in_date": "11-08-2022",
        "out_date": "23-08-2022"
      },
      {
        "product_no": "V_DB_KCS_3",
        "style_code": 142,
        "color_code": 176,
        "performance": 20,
        "quantity": 40,
        "current_progress": 15,
        "in_date": "24-08-2022",
        "out_date": "30-08-2022"
      }
    ],
    "Chuyền 2": [
      {
        "product_no": "V_DB_KCS_2",
        "style_code": 142,
        "color_code": 176,
        "quantity": 40,
        "performance": 20,
        "current_progress": 15,
        "in_date": "11-08-2022",
        "out_date": "23-08-2022"
      },
      {
        "product_no": "V_DB_KCS_3",
        "style_code": 142,
        "color_code": 176,
        "quantity": 40,
        "performance": 20,
        "current_progress": 15,
        "in_date": "24-08-2022",
        "out_date": "30-08-2022"
      }
    ]
}

</script>

<template>
  <div class="table">
    <table>
    <thead>
      <tr>
        <th class="abc" style="border-bottom: none;"></th>
        <th v-for="(colspan, month) in months" :colspan="colspan" class="month-date">
          {{ month }}
        </th>
      </tr>
      <tr class="weeks">
        <th class="abc" style="border-top: none;border-bottom: none;"></th>
        <th v-for="(colspan, week) in weeks" :colspan="colspan">
          {{ week }}
        </th>
      </tr>
      <tr class="days">
        <th class="abc" style="border-top: none; width: 300px">
          <table style="border: none;">
            <tbody>
              <tr>
                <td style="border: none;">PO No.</td>
                <td style="border: none;">Số ngày</td>
              </tr>
            </tbody>
          </table>
        </th>
        <th v-for="date in dates">
          {{ date }}
        </th>
      </tr>
    </thead>
    <tbody v-for="(products, department_name) in planedData" class="row">
        <tr class="days">
          <th class="abc">
            {{department_name}}
          </th>
          <td colspan=30>
          </td>
        </tr>
        <tr v-for="product in products">
          <th>
            <table style="border: none;">
              <tbody>
                <tr>
                  <td style="border: none;">{{product.product_no}}</td>
                  <td style="border: none;">{{product.quantity / product.performace}}</td>
                </tr>
              </tbody>
            </table>
          </th>
          <td v-for="date in dates" :class="(date >= product.in_date && date <= product.out_date) ? `bg-color` : ``">
          </td>
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
  &--header  {
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
.body-items{
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
