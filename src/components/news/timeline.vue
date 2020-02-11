<template>
  <div class="time_line_box">
    <div class="time_box">{{time|formatTime}}</div>
    <div class="text_box">
      <a :href="url">
        <slot></slot>
      </a>
    </div>
  </div>
</template>
<script>
// @ is an alias to /src
export default {
  name: "timeline",
  props: ["time", "url"],
  data() {
    return {};
  },
  filters: {
    formatTime(val) {
      let t = new Date((val + "000") / 1);
      function f(val) {
        return val > 9 ? val : "0" + val;
      }
      return (
        f(t.getMonth() + 1) +
        "月" +
        f(t.getDate()) +
        "日" +
        "  " +
        f(t.getHours()) +
        ":" +
        f(t.getMinutes())
      );
    }
  },
  components: {}
};
</script>
<style lang="less">
.time_line_box {
  padding-left: 20px;
  padding-bottom: 8px;
  .time_box {
    color: #999;
    font-size: 14px;
    position: relative;
    &::before {
      content: "";
      display: inline-block;
      position: absolute;
      width: 5px;
      height: 5px;
      border-radius: 50%;
      background: rgb(96, 205, 224);
      box-shadow: 0 0 0 3px rgb(131, 225, 241);
      left: -16px;
      top: 7px;
    }
  }
  .text_box {
    // width: 680px;
    height: 40px;
    line-height: 40px;
    border-radius: 5px;
    background: rgb(243, 239, 239);
    padding-left: 10px;
    box-sizing: border-box;
    margin: 7px 0px;
    position: relative;
    a {
      color: #333;
      font-size: 20px;
      font-weight: 600;
      text-decoration: none;
      display: block;
    }
    &::before {
      content: "";
      display: block;
      position: absolute;
      width: 1px;
      height: 65px;
      background: #eee;
      top: -7px;
      left: -14px;
    }
  }
}
</style>