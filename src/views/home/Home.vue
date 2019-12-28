<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <scroll
      class="content"
      ref="scroll"
      :probe-type="3"
      @scroll="contentScroll"
      :pull-up-load="true"
      @pullingUp="loadMore"
    >
      <home-swiper :banners="banners" />
      <recommend-view :recommends="recommends" />
      <feature-view />
      <tab-contorl :titles="['流行','精选','优惠']" />
      <ul>
        <li>1个li</li>
        <li>2个li</li>
        <li>3个li</li>
        <li>4个li</li>
        <li>5个li</li>
        <li>6个li</li>
        <li>7个li</li>
        <li>8个li</li>
        <li>9个li</li>
        <li>10个li</li>
        <li>11个li</li>
        <li>12个li</li>
        <li>13个li</li>
        <li>14个li</li>
        <li>15个li</li>
        <li>16个li</li>
        <li>17个li</li>
        <li>18个li</li>
        <li>19个li</li>
        <li>20个li</li>
        <li>21个li</li>
        <li>22个li</li>
        <li>23个li</li>
        <li>24个li</li>
        <li>25个li</li>
        <li>26个li</li>
        <li>27个li</li>
        <li>28个li</li>
        <li>29个li</li>
        <li>30个li</li>
        <li>31个li</li>
        <li>32个li</li>
        <li>33个li</li>
        <li>34个li</li>
        <li>35个li</li>
        <li>36个li</li>
        <li>37个li</li>
        <li>38个li</li>
        <li>39个li</li>
        <li>40个li</li>
        <li>41个li</li>
        <li>42个li</li>
        <li>43个li</li>
        <li>44个li</li>
        <li>45个li</li>
        <li>46个li</li>
        <li>47个li</li>
        <li>48个li</li>
        <li>49个li</li>
        <li>50个li</li>
        <li>51个li</li>
        <li>52个li</li>
        <li>53个li</li>
        <li>54个li</li>
        <li>55个li</li>
        <li>56个li</li>
        <li>57个li</li>
        <li>58个li</li>
        <li>59个li</li>
        <li>60个li</li>
        <li>61个li</li>
        <li>62个li</li>
        <li>63个li</li>
        <li>64个li</li>
        <li>65个li</li>
        <li>66个li</li>
        <li>67个li</li>
        <li>68个li</li>
        <li>69个li</li>
        <li>70个li</li>
        <li>71个li</li>
        <li>72个li</li>
        <li>73个li</li>
        <li>74个li</li>
        <li>75个li</li>
        <li>76个li</li>
        <li>77个li</li>
        <li>78个li</li>
        <li>79个li</li>
        <li>80个li</li>
        <li>81个li</li>
        <li>82个li</li>
        <li>83个li</li>
        <li>84个li</li>
        <li>85个li</li>
        <li>86个li</li>
        <li>87个li</li>
        <li>88个li</li>
        <li>89个li</li>
        <li>90个li</li>
        <li>91个li</li>
        <li>92个li</li>
        <li>93个li</li>
        <li>94个li</li>
        <li>95个li</li>
        <li>96个li</li>
        <li>97个li</li>
        <li>98个li</li>
        <li>99个li</li>
        <li>100个li</li>
      </ul>
      <button @click="toTop">点我</button>
    </scroll>
  </div>
</template>

<script>
import HomeSwiper from "./childComps/HomeSwiper";
import RecommendView from "./childComps/RecommendView";
import FeatureView from "./childComps/FeatureView";

import NavBar from "components/common/navbar/NavBar";
import TabContorl from "components/content/tabControl/TabControl";
import Scroll from "components/common/scroll/Scroll";

import { getHomeMultidata, getProductData } from "network/home";
import { debounce } from "common/utils";
export default {
  name: "Home",
  components: {
    HomeSwiper,
    RecommendView,
    FeatureView,
    NavBar,
    TabContorl,
    Scroll
  },
  data() {
    return {
      banners: [],
      recommends: [],
      goods: {
        pop: { page: 0, list: [] },
        news: { page: 0, list: [] },
        sell: { page: 0, list: [] }
      }
    };
  },
  created() {
    this.getHomeMultidata();
    this.$bus.$on("aaa", () => {
      console.log("监听到了aaa事件，要在这里处理事情");
    });
  },
  mounted() {
    const result = debounce(this.getHome, 200);
    this.$bus.$on("imgLoad", () => {
      result();
    });
  },
  methods: {
    loadMore() {
      console.log("上拉加载更多");
      setTimeout(() => {
        //在这里发送请求，加载更多数据
        //处理数据之后，要调用一下这个方法，上拉事件才会被刷新
        this.$refs.scroll.finishPullUp();
      }, 1000);
    },
    getHomeMultidata() {
      getHomeMultidata().then(res => {
        this.banners = res.data.banner.list;
        this.recommends = res.data.recommend.list;
      });
    },
    toTop() {
      this.$refs.scroll.scrollTo(0, 0, 5000);
    },
    contentScroll(position) {},
    getHome() {
      axios.get("xxxx");
    }
  }
};
</script>

<style scoped>
#home {
  padding-top: 44px;
  height: 100vh;
}
.home-nav {
  background-color: var(--color-tint);
  color: #fff;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 9;
}
.tab-control {
  position: sticky;
  top: 44px;
}
.content {
  position: absolute;
  top: 44px;
  bottom: 49px;
  left: 0;
  right: 0;
}
</style>