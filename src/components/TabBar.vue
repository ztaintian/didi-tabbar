<template>
  <div class="wrapper" ref="wrapper">
    <div class="content">
      <div
        @click="tab($event, index)"
        :class="[activeIndex === index?'active':'', 'item']"
        v-for="(item, index) in menuList"
        :key="index"
      >{{item.name}}</div>
    </div>
  </div>
</template>

<script>
import Bscroll from "better-scroll";
export default {
  data() {
    return {
      activeIndex: 0,
      menuList: [
        {
          name: "快车"
        },
        {
          name: "顺风车"
        },
        {
          name: "礼橙专车"
        },
        {
          name: "出租车"
        },
        {
          name: "豪华车"
        },
        {
          name: "拼车"
        },
        {
          name: "修车"
        }
      ]
    };
  },
  mounted() {
    this.$nextTick(() => {
      this.scroll = new Bscroll(this.$refs.wrapper, {
        scrollX: true,
        click: true
      });
    });
  },
  methods: {
    tab(event, index) {
      console.log(event.clientX);
      var wrapper = this.$refs.wrapper;
      var clientX = document.body.clientWidth;
      this.activeIndex = index;
      console.log(index, this.menuList.length);
      if (2 < index && event.clientX > 180 && index< this.menuList.length - 2) {
        this.scroll.scrollBy(-70, 0, 700, "bounce");
      }
    }
  }
};
</script>

<style lang="stylus">
.wrapper {
  width: 100%;
  overflow: hidden;

  .content {
    width: 490px;

    .item {
      display: inline-block;
      float: left;
      text-align: center;
      width: 70px;
      height: 40px;
    }

    .active {
      color: #0767BE;
    }
  }
}
</style>