<template>
	<div class="header">
		<div class="top-wrapper">
			<div class="back-wrapper">
				<span class="icon-arrow_lift"></span>
			</div>

			<form class="search-wrapper">
				<span class="search-icon"></span>
				<input class="search-bar" placeholder="搜尋店內商品" type="text" >
			</form>

			<div class="more-wrapper">
				<a class="spelling-bt" href="">拼單</a>
				<div class="more-bt">
					<i class="s-radius"></i>
					<i class="s-radius"></i>
					<i class="s-radius"></i>
				</div>
			</div>

		</div>
		
		<!--主體內容-->
		<div class="content-wrapper">
			<div class="icon" :style="head_bg"></div>
			<div class="name">
				<h3>{{poiInfo.name}}</h3>
			</div>
			<div class="collect">
				<img src="./star.png">
				<span>收藏</span>
			</div>
		</div>


        <!--公告內容-->
		<div class="bulletin-wrapper" @click="showBulletin">
			<img :src="poiInfo.discounts2[0].icon_url" class="icon" v-if="poiInfo.discounts2">
			<span class="text" v-if="poiInfo.discounts2">
				{{poiInfo.discounts2[0].info}}
			</span>
			<div class="detail" v-if="poiInfo.discounts2">
				{{poiInfo.discounts2.length}}個活動
				<span class="icon-keyboard_arrow_right"></span>
			</div>
		</div>

	    <!--背景-->
		<div class="bg-wrapper" :style="content_bg"></div>

		<!-- 公告詳情頁 -->
		<transition name="detail">	
	 		<div class="bulletin-detail" v-show="isShow">
	 			<div class="detail-wrapper">
	 				<div class="main-wrapper" :style="detail_bg">
	 					<div class="icon" :style="head_bg"></div>
	 					<h3 class="name">{{poiInfo.name}}</h3>
	 					<!-- 評價 -->
						<div class="score">
							<Star :score='poiInfo.wm_poi_score'></Star>
							<span>{{poiInfo.wm_poi_score}}</span>
						</div>

	 					<p class="tip">
	 						{{poiInfo.min_price_tip}} <i>|</i>
	 						{{poiInfo.shipping_fee_tip}}<i>|</i>
	 						{{poiInfo.delivery_time_tip}}
	 					</p> 
	 					<p class="time">
	 						配送時間:
	 						{{poiInfo.shipping_time}}
	 					</p>
	 					<div class="discounts" v-if="poiInfo.discounts2">
	 						<p v-for="(item, key) in poiInfo.discounts2">
	 							<img :src="poiInfo.discounts2[key].icon_url">
	 							<span>{{poiInfo.discounts2[key].info}}</span>
	 						</p>
	 					</div>
	 				</div>
	 				<div class="close-wrapper">
	 					<span class="icon-close" @click="closeBulletin"></span>
	 				</div>
	 			</div>
	 		</div>
 	    </transition>

	</div>
</template>
<script>

	import Star from "components/Star/Star"

	export default{
		data(){
			return {
				isShow: false //公告詳情顯示
			}
		},
		components:{
			Star
		},
		props: {
			poiInfo:{
				type:Object,
				default:{}
			}
		},
		computed: {
			content_bg(){
				return "background-image: url("+this.poiInfo.head_pic_url+")"
			},
			head_bg(){
				return "background-image: url("+this.poiInfo.pic_url+")"
			},
			detail_bg(){
				return "background-image: url("+this.poiInfo.poi_back_pic_url+")"
			}
		},
		methods:{
			showBulletin(){
				this.isShow = true;
			},
			closeBulletin(){
				this.isShow = false;
			}
		}
	}
</script>
<style>
    @import url("../../common/styles/icon.css");
	@import url("Header.css");
</style>