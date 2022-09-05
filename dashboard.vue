<template>
  <div id="dashboard">
    <div class="dash--absolute">
      <div class="dash--left">
        <img src="@/assets/icon-clock.svg" alt="clock" />
        <span>15:02</span>
      </div>
      <div class="dash--right">
        <span>LINE 10</span>
        <marquee-text>{{ text }}</marquee-text>
        <span>{{ text }}</span>
        <!-- <div class="marquee">
          <p :style="{ animationDuration: `${text.length * 0.5}s` }">
            {{ text }}
          </p>
        </div> -->
      </div>
    </div>
    <div class="dash--top dash--item">
      <div class="tag">KẾ HOẠCH</div>
      <div class="number-top">2691</div>
    </div>
    <div class="dash--bottom dash--item">
      <div class="dash--box">
        <div class="box-content">
          <div class="box--title">
            <img src="@/assets/icon-dash.svg" alt="icon" />
            <span>THỰC HIỆN</span>
          </div>
          <div class="number">2691</div>
        </div>
      </div>
      <div class="dash--box box--am">
        <div class="box-content">
          <div class="box--title">
            <img src="@/assets/icon-dash-2.svg" alt="icon" />
            <span>CÒN LẠI</span>
          </div>
          <div class="number">-1600</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import MarqueeText from 'vue-marquee-text-component';
export default {
  name: 'App',
  components: {
    MarqueeText,
  },
  data() {
    return {
      text: '45005193-2',
    };
  },
};
</script>

<style>
body {
  margin: 0;
  font-family: 'Inter';
}

.tag {
  font-style: normal;
  font-weight: 700;
  font-size: 140px;
  display: inline-block;
  background: #7958c0;
  border-radius: 41px;
  color: white;
  padding: 40px 100px;
}

.number-top {
  margin-top: 20px;
  font-size: 500px;
  font-weight: bold;
  color: #7958c0;
}

.dash--top {
  position: relative;
  top: 150px;
  height: 45%;
  text-align: center;
}

.dash--bottom {
  padding: 50px;
  height: 50%;
  display: flex;
}

.dash--box {
  width: calc(50% - 25px);
  background: #ff8d26;
  display: inline-block;
  border-radius: 80px;
  height: 95%;
}

.dash--box.box--am {
  background: #ff053c;
}
.dash--box.box--dm {
  background: #24890b;
}

.dash--box + .dash--box {
  margin-left: 50px;
}

#dashboard {
  height: 100vh;
  width: 100vw;
  overflow: hidden;
  position: relative;
}
.box-content {
  height: 100%;
}

.box-content,
.box--title {
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-items: center;
}
.box--title {
  flex-flow: row;
  font-size: 120px;
  color: white;
}
.box--title img {
  width: 120px;
  width: 120px;
  margin-right: 30px;
}

.number {
  font-size: 350px;
  color: white;
}
.dash--absolute {
  position: absolute;
  display: flex;
  justify-content: space-between;
  align-items: center;
  top: 50px;
  right: 0;
  left: 0;
  height: 300px;
  padding: 0 50px;
}
.dash--left img {
  width: 155px;
  margin-right: 15px;
}
.dash--left {
  display: flex;
  align-items: center;
  font-size: 165px;
  font-weight: bold;
  color: #2f3a4d;
}
.dash--right {
  text-align: right;
  display: flex;
  flex-flow: column;
  color: #2f3a4d;
  font-weight: 700;
  font-size: 130px;
  line-height: 157px;
}

@media screen and (max-width: 3199px) {
  .dash--right {
    font-size: 80px;
  }
  .tag {
    font-size: 100px;
  }

  .dash--left {
    font-size: 100px;
  }
  .number-top {
    font-size: 350px;
  }
  .number {
    font-size: 200px;
  }
}
@media screen and (max-width: 2199px) {
  .dash--left img {
    width: 55px;
  }

  .dash--right {
    font-size: 40px;
    line-height: 50px;
  }
  .tag {
    font-size: 50px;
  }
  .box--title {
    font-size: 90px;
  }
  .dash--left {
    font-size: 50px;
  }
  .number-top {
    font-size: 200px;
  }
  .number {
    font-size: 100px;
  }
}
/* .marquee {
  height: 50px;
  overflow-y: hidden;
  overflow-x: scroll;
  position: relative;
}

.marquee p {
  position: absolute;
  width: 100%;
  height: 100%;
  margin: 0;
  line-height: 50px;
  text-align: center;
  transform: translateX(100%);
  animation: scroll-left 10s linear infinite;
}

@-moz-keyframes scroll-left {
  0% {
    -moz-transform: translateX(100%);
  }
  100% {
    -moz-transform: translateX(-100%);
  }
}

@-webkit-keyframes scroll-left {
  0% {
    -webkit-transform: translateX(100%);
  }
  100% {
    -webkit-transform: translateX(-100%);
  }
}

@keyframes scroll-left {
  0% {
    -moz-transform: translateX(100%);
    -webkit-transform: translateX(100%);
    transform: translateX(100%);
  }
  100% {
    -moz-transform: translateX(-100%);
    -webkit-transform: translateX(-100%);
    transform: translateX(-100%);
  }
} */
</style>
