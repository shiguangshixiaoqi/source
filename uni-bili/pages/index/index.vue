<template>
	<view>
		<view>
			<swiper circular autoplay :interval="3000" :duration="500" indicator-dots style="height: 350rpx;" 
			  indicator-color="rgba(255, 255, 255, 0.6)" indicator-active-color="#FFB6C1">
			  <swiper-item v-for="item in imgs" :key="item" >
			    <image :src="item" alt="" mode="widthFix" style="width: 100%;" />
			  </swiper-item>
			</swiper>
		</view>
		<view style="margin: 10px;">
		  
		  <view style="padding: 5px 10px; background-color: white; font-size: 12px; border-radius: 5px; display: flex; align-items: center;">
		    <uni-icons type="sound" size="20"></uni-icons>
		    <view>{{ notice }}</view>
		  </view>
		  <view style="background-color: white; margin: 5px 0; border-radius: 5px;padding: 10px 0;">
		    <uni-row>
		      <uni-col :span="6">
		        <view class="grid-item-box" @click="clickItem('时令水果')">
		          <image mode="widthFix" style="width: 50%;" src="../../static/imgs/水果.png"></image>
		          <text style="font-size: 13px; margin-top: 5px;">时令水果</text>
		        </view>
			  </uni-col>
			  <uni-col :span="6">
			    <view class="grid-item-box" @click="clickItem('品质肉禽')">
			      <image mode="widthFix" style="width: 50%;" src="../../static/imgs/肉禽.png"></image>
			      <text style="font-size: 13px; margin-top: 5px;">品质肉禽</text>
			    </view>
			  </uni-col>
			  <uni-col :span="6">
			    <view class="grid-item-box" @click="clickItem('新鲜水产')">
			      <image mode="widthFix" style="width: 50%;" src="../../static/imgs/海鲜.png"></image>
			      <text style="font-size: 13px; margin-top: 5px;">新鲜水产</text>
			    </view>
			  </uni-col>
			  <uni-col :span="6">
			    <view class="grid-item-box" @click="clickItem('蔬菜蛋品')">
			      <image mode="widthFix" style="width: 50%;" src="../../static/imgs/蔬菜.png"></image>
			      <text style="font-size: 13px; margin-top: 5px;">蔬菜蛋品</text>
			    </view>
			  </uni-col>
			</uni-row>
		  </view>
		  
		  <view style="margin: 5px 0; font-size: 12px;">
		    <uni-row :gutter='10'>
		      <uni-col :span='12' v-for="item in goodsList" :key="item.name">
		        <view style="margin-bottom: 5px; background-color: white; padding: 10px; border-radius: 10px;">
		          <image :src="item.img" mode="widthFix" style="width: 100%;"></image>
		          <view class="lineEllipsis">{{ item.name }}</view>
		          <view style="color: red; margin-top: 5px; font-weight: bold; font-size: 14px;">￥{{ item.price }}</view>
		          <view style="text-align: right;"><uni-icons type="plus" size="25" style="color: #666;" @click="addCart(item)"></uni-icons></view>
		        </view>
		      </uni-col>
		    </uni-row>
		  </view>
				
		  
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				imgs: [
					"https://m.360buyimg.com/babel/jfs/t20260719/200274/27/38564/103066/64b8a92bF9ff64827/86b0873317ff1670.jpg",
					"https://m.360buyimg.com/babel/jfs/t20260720/127672/11/35840/78112/64ba27ceF7f110966/ec2e2c6c366fa94c.jpg",
					"https://m.360buyimg.com/babel/jfs/t20260713/161699/23/38353/136417/64b0a7dbF5e25fcdd/ba43ddee33949c1c.png"
					
				],
				notices: [
				  {content: "亲哥哥哥今晚电商直播真的很棒棒噢"},
				  {content: "啊真的是 uniapp有手就会啊"},
				  {content: "真的吗？这么easy？"},
				  {content: "不信你去看看青哥哥的教程呗"},
				],
				notice: '',
				goodsList: [
				  { name: '固伦天原 农家土鸡蛋现捡新鲜谷物虫草柴鸡蛋初生蛋简装 20枚装', price: 19.9, 
				    img: 'https://m11.360buyimg.com/babel/s522x456_jfs/t1/147254/20/37798/87316/6458689bF5bb085ce/f1177ea39ce03322.jpg' },
				  { name: '大口鲜 熟冻帝王蟹礼盒装 海鲜礼包 整只 3.2-3.6斤现货 海产礼盒', price: 79.9,
				    img: 'https://m11.360buyimg.com/babel/s522x456_jfs/t1/210206/31/4285/246694/61614b6bE8e495865/1b801854736d9736.jpg' },
				  { name: '仙泉湖三去星洲红 500g*1条 净膛冷冻罗非鱼海鲜食材 刺少', price: 99.9,
				    img: 'https://m11.360buyimg.com/babel/s522x456_jfs/t1/139489/10/25554/185007/61d68c23Eef30e5c7/86fac8623b27de32.jpg' },
				  { name: '洛川苹果80mm大果 净重4.2斤 陕西延安红富士新鲜时令生鲜水果', price: 19.9,
				    img: 'https://m11.360buyimg.com/babel/s561x561_jfs/t1/206463/33/3190/152008/6155d86eE00924ef0/8e955e07ea8d1942.jpg' },
				  { name: '妙果樱广西青芒新鲜水果大青芒果当季时令生鲜芒果 3斤大果（单果250g+）', price: 29.9,
				    img: 'https://m11.360buyimg.com/babel/s561x561_jfs/t1/142695/20/37414/69619/64b8d41bF0e06aea0/8961fde6fe2b619b.jpg' },				
				]

			}
		},
		onLoad() {
			this.loadNotice()

		},
		methods: {
			loadNotice() {
			  let i = 0
			  this.notice = this.notices[i++].content  // 默认显示一个公告  i = 0
			  setInterval(() => {
			    this.notice = this.notices[i++].content   // i = 1,2,3
			    if (i === this.notices.length) {
			      i = 0
			    }
			  }, 5000)
			},
			clickItem(item) {
				console.log(item)
			},
			addCart(item) {
				console.log(item.name)
			}
			
		}
	}
</script>

<style>
	.grid-item-box {
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;
		}
	.lineEllipsis {
			word-break: break-all;
			text-overflow: ellipsis;
			display: -webkit-box;
			-webkit-box-orient: vertical;
			-webkit-line-clamp: 2;
			/* 超出2行省略 */
			overflow: hidden;
		}
</style>
