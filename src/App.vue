<script setup>
import MarqueeText from 'vue-marquee-text-component'
</script>

<template>
  <div class="container">
    <div class="col-6">
      <div class="info-wrapper">
        <div class="info--top d-flex">
          <div class="left">
          <div class="time"><i class="icon"></i> 10:02</div>
          </div>
          <div class="right">
            <div>Line 10</div>
            <div v-if="true">123122222</div>
            <MarqueeText v-else class="text-run">12312</MarqueeText>
          </div>
        </div>
        <div class="info--body">
          <div class="info--body-top">
            <div class="tag">Ke hoach</div>
            <div class="number">2691</div>
          </div>
          <div class="info-body-footer">
            <div class="info--box">
              <div class="info--box-header">
                <div class="text"><i class="icon"></i>Thuc Hien</div>
                <div class="number">1900</div>
              </div>
            </div>
            <div class="info--box is-am">
              <div class="info--box-header">
                <div class="text"><i class="icon"></i>Con lai</div>
                <div class="number">-1600</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="col-6">
      <div class="info-wrapper">
        <div class="info--top d-flex">
          <div class="left">
          <div class="time"><i class="icon"></i> 15:02</div>
          </div>
          <div class="right">
            <div>Line 10</div>
            <div v-if="true">123122222</div>
            <MarqueeText v-else class="text-run">12312</MarqueeText>
          </div>
        </div>
        <div class="info--body">
          <div class="info--body-top">
            <div class="tag">Ke hoach</div>
            <div class="number">2691</div>
          </div>
          <div class="info-body-footer">
            <div class="info--box">
              <div class="info--box-header">
                <div class="text"><i class="icon"></i>Thuc Hien</div>
                <div class="number">1900</div>
              </div>
            </div>
            <div class="info--box is-dm">
              <div class="info--box-header">
                <div class="text"><i class="icon"></i>Con lai</div>
                <div class="number">+1600</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<style lang="scss">
  $mainPurple: #7958C0;
  $mainYello: #FF8D26;
  $mainRed: #FF033D;
  .container {
    min-height: 100vh;
    width: 100%;
    display: flex;
    background: #f5f5f5;
  }

  .col-6 {
    flex: 0 0 50%;
  }
  .info-wrapper {
    background-color: white;
    margin: 0 15px;
    padding: 15px;

    .icon {
      display: inline-block;
      width: 15px;
      height: 15px;
      background: red;
    }

    .d-flex {
      display: flex;
    }

    .info--top {
      font-weight: bold;
      justify-content: space-between;

      .right {
        width: 20%;
        text-align: right;
        text-transform: uppercase;
      }

      .text-run {
        max-width: 30%;
      }
    }
  }
  .tag {
    text-transform: uppercase;
    padding: 5px 10px;
    background: $mainPurple;
    color: white;
    display: inline-block;
    border-radius: 3px;
    font-size: 14px;
  }
  .info--body-top {
    position: relative;
    top: -20px;
    text-align: center;
    .number {
      font-size: 48px;
      font-weight: bold;
      color: $mainPurple;
    }
  }
  .info-body-footer {
    display: flex;
    justify-content: space-between;
  }
  .info--box {
    border-radius: 5px;
    background: $mainYello;
    flex: 0 0 49%;
    display: inline-block;

    &.is-am {
      background-color: $mainRed;
    }

    &.is-dm {
      background-color: #25890A;
    }
  }

  .info--box-header {
    text-align: center;
    text-transform: uppercase;
    padding: 30px;
    color: white;

    .number {
      font-size: 36px;
    }
  }
</style>
