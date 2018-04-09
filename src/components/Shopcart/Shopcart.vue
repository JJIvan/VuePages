<template>
	<div class="shopcart" :class="{'highlight':totalCount>0}">
		<div class="content-left">
			<div class="logo-wrapper" :class="{'highlight':totalCount>0}">
				<span class="icon-shopping_cart logo" :class="{'highlight':totalCount>0}"></span>
				<i class="num" v-show="totalCount">{{totalCount}}</i>
			</div>
			<div class="desc-wrapper">
				<p class="total-price" v-show="totalPrice">${{totalPrice}}</p>
				<p class="tip" :class="{'highlight':totalCount>0}">另需{{shippingfeetip}}</p>
			</div>
		</div>
		<div class="content-right" :class="{'highlight':totalCount>0}">
			{{payStr}}
		</div>
	</div>
</template>


<script>
	export default{
		props:{
			minpricetip:{
				type:String,
				default:''
			},
			shippingfeetip:{
				type:String,
				default:''
			},
			selectFoods:{
				type:Array,
				default(){
					return [

					];
				}
			}
		},
		computed:{
			// 總個數
			totalCount(){
				let num = 0;
				this.selectFoods.forEach( (food)=>{
					num += food.count;
				} )
				return num;
			},
			// 總金額
			totalPrice(){
				let total = 0;
				this.selectFoods.forEach( (food)=>{
					total += food.min_price * food.count;
				} )
				return total;
			},
			// 結算按鈕
			payStr(){
				if(this.totalCount > 0){
					return "去結算";
				}else{
					return this.minpricetip;
				}
			}
		}
	}
</script>


<style>
	@import url(Shopcart.css);
</style>