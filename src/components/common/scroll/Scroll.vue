<template>
  <div class="wrapper" ref="wrapper">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import BScroll from "better-scroll";

export default {
  name: "Scroll",
  props: {
    probeType: {
      //监听实时滚动事件
      type: Number,
      default: 0
    },
    pullUpLoad: {
      //监听上拉加载更多
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      scroll: null
    };
  },
  mounted() {
    console.log(this.$refs.wrapper);
    this.getScorll();
    this.$bus.$emit("aaa");
  },
  methods: {
    getScorll() {
      this.scroll = new BScroll(this.$refs.wrapper, {
        click: true,
        probeType: this.probeType,
        pullUpLoad: true
      });
      //当传递过来的值是2或者是3的时候才开启监听滚动事件
      if (this.probeType === 2 || this.probeType === 3) {
        //监听实时滚动事件，并且通过$emit把这个属性传递出去，父组件监听这个事件就可以拿到值
        this.scroll.on("scroll", position => {
          this.$emit("scroll", position);
        });
      }

      //当传递过来的pullUpLoad为true的时候才开启监听上拉加载更多
      if (this.pullUpLoad) {
        //监听上拉加载更多
        this.scroll.on("pullingUp", () => {
          this.$emit("pullingUp");
        });
      }
    },
    scrollTo(x, y, time = 300) {
      //判断this.scroll是否被创建了
      this.scroll && this.scroll.scrollTo(x, y, time);
    },
    //上拉加载只能调用一次，如果想多次调用，每次都要先调用finishPullDown这个方法
    finishPullUp() {
      this.scroll.finishPullUp();
    },
    //重新计算scrollerHeight可滚动区域高度
    refresh() {
      //判断this.scroll是否被创建了
      this.scroll && this.scroll.refresh();
    },
    getScrollY(){
      return this.scroll ? this.scroll.y : 0
    }
  }
};
</script>

<style scoped>
</style>