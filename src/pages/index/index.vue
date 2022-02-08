<template>
  <div class="wrapper">
    <div class="header-wrapper">
      <div class="header-title">
        <span>空气质量 良好</span>
        <span>南宁市</span>
      </div>
      <div class="header-text">
        <span>55</span>
        <span>阴天</span>
      </div>
      <div class="weather-advice">空气质量良好，外出活动无需刻意防护</div>
    </div>

    <div class="body-wrapper">
      <div class="body">
        <div class="data-wrapper">
          <div class="data">
            <img class="data-logo" src="/static/images/temperature.png" />
            <div class="data-text">
              <div class="data-title">温度</div>
              <div class="data-value">26℃</div>
            </div>
          </div>

          <div class="data">
            <img class="data-logo" src="/static/images/humidity.png" />
            <div class="data-text">
              <div class="data-title">湿度</div>
              <div class="data-value">69%</div>
            </div>
          </div>
        </div>
        <div class="data-wrapper">
          <div class="data">
            <img class="data-logo" src="/static/images/illuminance.png" />
            <div class="data-text">
              <div class="data-title">光照度</div>
              <div class="data-value">1256lux</div>
            </div>
          </div>

          <div class="data">
            <img class="data-logo" src="/static/images/light.png" />
            <div class="data-text">
              <div class="data-title">电灯</div>
              <div class="data-value">
                <switch color="#1296db" />
              </div>
            </div>
          </div>
        </div>
        
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {},

  components: {},

  methods: {},

  created() {
    // let app = getApp()
  },
};
</script>

<style lang="scss" scoped>
.wrapper {
  padding: 15px;
  .header-wrapper {
    padding: 15px 30px;
    background-color: #1296db;
    border-radius: 20px;
    color: #fff;
    box-shadow: #b6b5b5 3px 3px 5px;
    .header-title {
      display: flex;
      justify-content: space-between;
    }
    .header-text {
      font-size: 32px;
      font-weight: 400;
      display: flex;
      justify-content: space-between;
    }
    .weather-advice {
      margin-top: 20px;
      font-size: 12px;
    }
  }

  .data-wrapper {
    margin-top: 20px;
    display: flex;
    justify-content: space-between;

    .data {
      background-color: #fff;
      width: 45%;
      height: 80px;
      display: flex;
      justify-content: space-around;
      border-radius: 20px;
      padding: 2px 6px;
      margin: 4px;
      box-shadow: #b6b5b5 2px 2px 4px;
      .data-logo {
        height: 40px;
        width: 40px;
        margin: 15px 0px;
      }
      .data-text {
        margin: 15px 0px;
        color: #7f7f7f;
        .data-value {
          font-size: 26px;
        }
      }
    }
  }
}
</style>
