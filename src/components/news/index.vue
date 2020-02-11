<template>
  <div class="news_box">
    <h2>实时播报</h2>
    <timeline
      v-for="(item) in list"
      :key="item.time"
      :url="item.eventUrl"
      :time="item.eventTime"
    >{{item.eventDescription}}</timeline>
    <!-- <timeline></timeline> -->
  </div>
</template>
<script>
// @ is an alias to /src
import { getZbData } from "@/api";
import timeline from "./timeline";
export default {
  name: "news",
  data() {
    return {
      list: []
    };
  },
  created() {
    getZbData().then(data => {
      console.log(data);
      this.list = data.items;
    });
  },
  components: {
    timeline
  }
};
</script>
<style lang="less">
.news_box {
  width: 700px;
  margin: 20px auto;
  padding-bottom: 20px;
  h2 {
    padding: 0 0 20px 0;
  }
}
</style>