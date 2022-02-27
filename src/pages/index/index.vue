<template>
  <div class="wrapper">
    <div class="header-wrapper">
      <div class="header-title">
        <span>紫外线强度-{{ uvStrength }}</span>
        <span>{{ city }}</span>
      </div>
      <div class="header-text">
        <span>{{ Temp }}℃</span>
        <span>{{ weather }}</span>
      </div>
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
  data() {
    return {
      temp: 0,
      light: 0,

      Temp:0,
      city: "Requesting", //城市
      weather: "Requesting", //天气
      uvStrength:"Requesting"//紫外线强度
    };
  },

  onShow() {
    var that = this;
    //获取位置经纬度
    wx.getLocation({
      type: "wgs84",
      success(res) {
        console.log("获取位置成功");
        const latitude = res.latitude;
        const longitude = res.longitude;
        const key = "17437659bebb44ddb347044bc5de771b";

        //获取天气数据api接口地址
        wx.request({
          url: `https://api.seniverse.com/v3/weather/now.json?key=Skwkb_ygUiixRsnsj&location=${latitude}:${longitude}&language=zh-Hans&unit=c`,
          success(res) {
            console.log(res.data);
            const Data = res.data;
            // console.log(Data.results[0].location.name);
            that.city = Data.results[0].location.name;
            that.weather = Data.results[0].now.text;
            that.Temp = Data.results[0].now.temperature;
          },
        });

        //获取生活指数数据api接口地址
        wx.request({
          url: `https://api.seniverse.com/v3/life/suggestion.json?key=Skwkb_ygUiixRsnsj&location=${latitude}:${longitude}&language=zh-Hans`,
          success(res) {
            console.log(res.data);
            const Data = res.data;
            that.uvStrength = Data.results[0].suggestion.uv.brief;
            
          },
        });
      },
    });
  },

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
      margin-bottom:20px;
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
