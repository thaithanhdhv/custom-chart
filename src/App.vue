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
</script>
<template>
  <!-- <div class="chart">
    <div class="chart--left">
      <div class="space"></div>
      <div class="space"></div>
      <div class="line-desc">
        <div>Name</div>
        <div>Dates</div>
      </div>
      <div class="events-name">
        <div class="event--item">Chuyen 1</div>
        <div class="event--item">Chuyen 1 con</div>
        <div class="event--item">Chuyen 2 con</div>
        <div class="event--item">Chuyen 1</div>
        <div class="event--item">Chuyen 1 con</div>
        <div class="event--item">Chuyen 2 con</div>
        <div class="event--item">Chuyen 1</div>
        <div class="event--item">Chuyen 1 con</div>
        <div class="event--item">Chuyen 1 con</div>
        <div class="event--item">Chuyen 1 con</div>
      </div>
    </div>
    <div class="chart--right">
        <div class="chart--right--header">
          <div class="month">
            <div class="month--header">
              <div class="month--name">Thang 8, 2022</div>
              <div class="month--weeks">
                <div class="month--weeks--item" v-for="i of 4" :key="i">
                  <div class="month--weeks--name">Week {{ i }}</div>
                    <div class="month--weeks--dates">
                    <span class="month--dates--item" v-for="i of 7" :key="i">{{ i }}</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="month">
            <div class="month--header">
              <div class="month--name">Thang 8, 2022</div>
              <div class="month--weeks">
                <div class="month--weeks--item" v-for="i of 4" :key="i">
                  <div class="month--weeks--name">Week {{ i }}</div>
                    <div class="month--weeks--dates">
                    <span class="month--dates--item" v-for="i of 7" :key="i">{{ i }}</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="chart--right--body">
          <div class="body-items" v-for="i of 10" :key="i">i</div>
        </div>
    </div>
  </div> -->
  <div class="table">
    <table>
    <thead>
      <tr>
        <th class="abc">Teams</th>
        <th colspan="28" class="month-date">Month 1</th>
        <th colspan="28" class="month-date">Month 2</th>
      </tr>
      <tr class="weeks">
        <th class="abc">Teams</th>
        <th colspan="7">Week 1</th>
        <th colspan="7">Week 2</th>
        <th colspan="7">Week 3</th>
        <th colspan="7">Week 4</th>
        <th colspan="7">Week 1</th>
        <th colspan="7">Week 2</th>
        <th colspan="7">Week 3</th>
        <th colspan="7">Week 4</th>
      </tr>
      <tr class="days">
        <th class="abc">Teams</th>
        <th>1</th>
        <th>2</th>
        <th>3</th>
        <th>4</th>
        <th>5</th>
        <th>6</th>
        <th>7</th>
        <th>1</th>
        <th>2</th>
        <th>3</th>
        <th>4</th>
        <th>5</th>
        <th>6</th>
        <th>7</th>
        <th>1</th>
        <th>2</th>
        <th>3</th>
        <th>4</th>
        <th>5</th>
        <th>6</th>
        <th>7</th>
        <th>1</th>
        <th>2</th>
        <th>3</th>
        <th>4</th>
        <th>5</th>
        <th>6</th>
        <th>7</th>
        <th>1</th>
        <th>2</th>
        <th>3</th>
        <th>4</th>
        <th>5</th>
        <th>6</th>
        <th>7</th>
        <th>1</th>
        <th>2</th>
        <th>3</th>
        <th>4</th>
        <th>5</th>
        <th>6</th>
        <th>7</th>
        <th>1</th>
        <th>2</th>
        <th>3</th>
        <th>4</th>
        <th>5</th>
        <th>6</th>
        <th>7</th>
        <th>1</th>
        <th>2</th>
        <th>3</th>
        <th>4</th>
        <th>5</th>
        <th>6</th>
        <th>7</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <th>Milwaukee Brewers</th>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
      </tr>
       <tr>
        <th>Milwaukee Brewers</th>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
      </tr>
       <tr>
        <th>Milwaukee Brewers</th>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
      </tr>
       <tr>
        <th>Milwaukee Brewers</th>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
      </tr>
       <tr>
        <th>Milwaukee Brewers</th>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
      </tr>
       <tr>
        <th>Milwaukee Brewers</th>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>3</td>
        <td>3</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
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
  width: 200px;
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
</style>
