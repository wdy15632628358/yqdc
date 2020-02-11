<template>
  <div class="list_box">
    <ul class="til">
      <li class="sort">排名</li>
      <li class="name">城市名称</li>
      <li class="percent">{{data.myIndex ?'迁入':'迁出'}}</li>
    </ul>
    <ul class="body">
      <!-- 循环父组件传来的数据，然后渲染 -->
      <li v-for="(item,index) in data" :key="index" @click="go">
        <div class="sort">{{index+1}}</div>
        <div class="name">
          {{item.city_name}}
          <span>({{item.province_name}})</span>
        </div>
        <div class="percent">{{item.value}}%</div>
      </li>
    </ul>
  </div>
</template>
<script>
// @ is an alias to /src
export default {
  name: "mylist",
  props: ["data"],//接收父组件的数据
  data() {
    return {};
  },
  components: {},
  methods: {
    //点击跳转
    go(item) {
      window.open(
        "https://qianxi.baidu.com/?from=shoubai#city=" + item.city_code
      );
    }
  }
};
</script>
<style lang="less" scoped>
.list_box {
  width: 650px;
  margin: 20px auto;
  cursor: pointer;
  ul {
    list-style: none;
  }
  .til,
  .body li {
    display: flex;
    height: 50px;
    line-height: 50px;
    border-bottom: 1px solid #d5dbdf;
    .sort,
    .percent {
      width: 80px;
    }
    .name {
      flex: auto;
    }
  }
}
</style>