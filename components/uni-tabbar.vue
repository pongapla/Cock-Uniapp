<template>
	<view class="uni-margin-wrap">
		<swiper class="swiper" circular 
				:indicator-dots="indicatorDots" 
				:autoplay="autoplay" 
				:interval="interval"
				:duration="duration"
				vertical="true">
			<swiper-item>
				<view class="swiper-item uni-bg-red">A</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item uni-bg-green">B</view>
			</swiper-item>
			<swiper-item>
				<view class="swiper-item uni-bg-blue">C</view>
			</swiper-item>
		</swiper>
	</view>
	<view class="uni-tabbar">
		<view class="uni-flex uni-row">
			<view class="flex-item" v-for="(item, index) in footerItems" :key="index" @click="navigateTo(item.path)">
			    <uni-icons :type="item.icon" size="25"></uni-icons>
			</view>
		</view>
	</view>
	
</template>

<script>
import uniIcons from '@dcloudio/uni-ui/lib/uni-icons/uni-icons.vue';

export default {
  components: {
    uniIcons
  },
  data() {
    return {
      footerItems: [
        { icon: "home", path: "/pages/index/index" },
        { icon: "info", path: "/pages/about/about" },
		{ icon: "contact", path: "/pages/about/about" }
      ],
	    autoplay: true,
	    interval: 3000,
	    duration: 500
    };
  },
  methods: {
    navigateTo(path) {
		console.log(path);
      uni.switchTab({ url: path });
    },
	changeIndicatorDots(e) {
	            this.indicatorDots = !this.indicatorDots
	        },
	        changeAutoplay(e) {
	            this.autoplay = !this.autoplay
	        },
	        intervalChange(e) {
	            this.interval = e.target.value
	        },
	        durationChange(e) {
	            this.duration = e.target.value
	        }
  }
};
</script>

<style scoped>
  .uni-flex {
    display: flex;
    width: 100%; 
  }

  .uni-row {
    flex-direction: row; 
  }

  .flex-item {
    flex: 1; 
    text-align: center; 
    padding: 10px; 
    box-sizing: border-box; 
  }
  
  .uni-tabbar {
	position: fixed;
	background-color: #D3D3D3;
	bottom: 0;
	left: 0;
	width: 100%;
	z-index: 1000;
  }
  
  .swiper {
	margin-top: 4px;
	padding: auto;
  }
  
  .swiper-item {
	  margin: 0 4px 0 4px;
	  border: 1px solid royalblue;
	  height: 76px;
  }
  
  .uni-margin-wrap {
	height: 84px;
  }
  



</style>