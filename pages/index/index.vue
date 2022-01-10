<template>
	<view class="content">
		<view class="banner">
			<view class="banner_img" @click="aboutClosed = true">
				<image src="/static/images/banner.png" mode=""></image>
			</view>
			<view class="banner_about" v-if="aboutClosed">
				<view class="about_box">
					<view class="about_title">关于S石材</view>
					<view class="about_text" v-for="(item,index) in text" :key="index">{{ item }}</view>
					<view class="closed">
						<image src="../../static/images/packUp.png" mode=""></image>
						<view class="closed_text" @click="aboutClosed = false">收起</view>
					</view>
				</view>
			</view>
		</view>
		<view class="tabs_main">
			<view :class="[{fixedTop:hightTop},'todaysDeal']">
				<view class="customNavigation" :style="{ paddingTop: top+ 'px',lineHeight: height+ 'px'  }"
					v-if="hightTop">
					S石材推荐
				</view>
				<view class="tabs">
					<view class="one_tabs no-scrollbar" :style="{marginTop:(hightTop ? '20rpx' : '')}">
						<view class="one_tab_item" :style="{fontWeight: actice1 == index ? 600 : ''}"
							v-for="(item,index) in tabs1" :key="index" @click="actice1 = index">
							{{ item }}
						</view>
						<view class="underline"
							:style="{ left: (actice1 === 0 ? actice1*150 :  actice1*(150+120)) + 'rpx'  }">
						</view>
					</view>
					<view class="small_banner" v-if="!hightTop">
						<image src="../../static/images/small_banner.png" mode=""></image>
					</view>
					<view class="two_tabs no-scrollbar">
						<view :class="[{actice:actice2 == index},'two_tab_item']" v-for="(item,index) in tabs2"
							:key="index" @click="actice2 = index">
							{{ item }}
						</view>
					</view>
					<view class="three_tabs no-scrollbar" :style="{paddingBottom:(hightTop ? '20rpx' : '')}">
						<view :class="[{actice:actice3 == index},'three_tab_item']" v-for="(item,index) in tabs3"
							:key="index" @click="actice3 = index">
							{{ item }}
						</view>
					</view>
				</view>
			</view>

			<view class="main_items">
				<view class="item" v-for="(item,index) in list" :key="index">
					<image :src="item.imgUrl" class="items_main_img" mode=""></image>
					<view class="item_body">
						<view class="describe">
							<image :src="item.profile" class="portrait" mode=""></image>
							<view class="name">
								<view class="shopName">{{ item.shopName }}</view>
								<view class="tradeName">{{ item.tradeName }}</view>
							</view>
						</view>
						<view class="price">
							¥{{ item.price }}
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="contact_we" @click="freeTell">
			<image src="../../static/images/contact.png" mode=""></image>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				text: [
					'一、 石材:是指从沉积岩、岩浆岩、变质岩的天然岩体中开采的岩石。',
					'二、天然石材大体分为花岗岩、板岩、砂岩、石灰岩、火山岩等，随着科技的不断发展和进步，人造石的产品也不断日新月异石材早已经成为建筑、装饰、道路、桥梁建设的重要原料之一。'
				],
				aboutClosed: true,
				tabs1: ['人气推荐', '超赞商家', '热门商家', '人气推荐', '超赞商家', '热门商家'],
				actice1: 0,
				tabs2: ['中远石业', '联发石业', '欧式石业', '奥都石材', '永成石材', '中远石业'],
				actice2: 0,
				tabs3: ['PLUS', '蓝金沙', '黑金沙', '埃及米黄', 'PLUS', '蓝金沙'],
				actice3: 0,
				list: [{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					}, {
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					}, {
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					}, {
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					}, {
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					}, {
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					},
					{
						imgUrl: require('../../static/images/2020033.jpg'),
						profile: require('../../static/images/2020033.jpg'),
						shopName: '中远石业',
						tradeName: '蓝金沙KK0109-3',
						price: 114
					}
				],
				wmssjH: 0,
				hightTop: false,
				height: 0,
				top: 0
			}
		},
		async onReachBottom() {
			console.log("onReachBottom");
		},
		onLoad() {},
		onPageScroll: function(e) { //监听页面滚动
			let that = this
			//判断你滑动的高度大于你元素距离顶部的高度值
			if (that.wmssjH < e.scrollTop) {
				//固定
				that.hightTop = true
			} else {
				that.hightTop = false
			}
		},
		onReady() {
			let menuRect = wx.getMenuButtonBoundingClientRect()
			this.height = menuRect.height
			this.top = menuRect.top
			//在进入页面onReady()获取元素距离顶部的值
			const query = uni.createSelectorQuery().in(this);
			query.select('.todaysDeal').boundingClientRect(data => {
				//data.top获取距离顶部的值
				this.wmssjH = data.top
			}).exec()
		},
		methods: {
			freeTell() {
				wx.makePhoneCall({
					phoneNumber: '03123688777',
				})
			}
		}
	}
</script>
<style>
	page {
		background-color: #10504D;
	}
</style>
<style lang="scss" scoped>
	.no-scrollbar {
		&::-webkit-scrollbar {
			display: none;
		}
	}

	.content {
		.banner {
			.banner_img {
				width: 100%;

				>image {
					width: 100%;
					height: 600rpx;
				}
			}

			.banner_about {
				padding: 40rpx 46rpx;

				.about_box {
					color: #FFFFFF;
					padding: 28rpx 30rpx;
					background: #10504D;
					box-shadow: 0px 4rpx 8rpx 0px rgba(0, 0, 0, 0.15);
					border-radius: 30rpx;
					border: 2rpx solid #FFFFFF;

					.about_title {
						font-size: 32rpx;
						font-weight: 600;
						color: #FFFFFF;
						line-height: 44rpx;
						margin: 20rpx 0;
						text-align: center;
					}

					.about_text {
						font-size: 28rpx;
						color: #FFFFFF;
						line-height: 40rpx;
					}
				}

				.closed {
					margin-top: 24rpx;

					>image {
						width: 24rpx;
						height: 24rpx;
						display: flex;
						margin: 0 auto;
					}

					.closed_text {
						text-align: center;
						font-size: 24rpx;
						color: #FFFFFF;
						line-height: 34rpx;
					}
				}
			}

		}

		.tabs_main {
			color: #FFF;

			.todaysDeal {
				.customNavigation {
					text-align: center;
					font-size: 30rpx;
					font-weight: 600;
					color: #FFFFFF;
					line-height: 42rpx;
				}

				.tabs {
					padding: 0 46rpx;

					.one_tabs {
						position: relative;
						width: 704rpx;
						overflow-x: auto;
						display: flex;
						align-items: center;



						.one_tab_item {
							padding: 22rpx 0;
							flex-shrink: 0;
							font-size: 30rpx;
							color: #FFFFFF;
							line-height: 42rpx;
							margin-left: 150rpx;

							&:first-child {
								margin-left: 0;
							}
						}

						.underline {
							position: absolute;
							bottom: 0;
							width: 120rpx;
							height: 8rpx;
							background: #6CC1C5;
							transition: left .4s;
						}
					}

					.small_banner {
						width: 100%;
						height: 144rpx;
						margin-top: 28rpx;

						>image {
							width: 100%;
							height: 100%;
						}
					}

					.two_tabs {
						padding: 30rpx 0;
						width: 704rpx;
						overflow-x: auto;
						display: flex;
						align-items: center;

						.two_tab_item {
							font-size: 26rpx;
							color: #FFFFFF;
							line-height: 36rpx;
							margin-left: 64rpx;
							flex-shrink: 0;

							&.actice {
								color: #6CC1C5;
								font-weight: 600;
							}

							&:first-child {
								margin-left: 0;
							}
						}
					}

					.three_tabs {
						margin-bottom: 8rpx;
						width: 704rpx;
						overflow-x: auto;
						display: flex;
						align-items: center;

						.three_tab_item {
							font-size: 28rpx;
							color: #FFFFFF;
							line-height: 40rpx;
							margin-left: 24rpx;
							flex-shrink: 0;
							padding: 12rpx 38rpx 12rpx 40rpx;
							border-radius: 16rpx;
							border: 2rpx solid #FFFFFF;

							&.actice {
								padding: 12rpx 42rpx 12rpx 46rpx;
								background: #6CC1C5;
								border: none;
							}

							&:first-child {
								margin-left: 0;
							}
						}
					}
				}


				&.fixedTop {
					background: #287776;
					width: 100%;
					position: fixed;
					left: 0;
					top: 0;
					z-index: 999;
				}
			}



			.main_items {
				display: flex;
				justify-content: space-between;
				flex-wrap: wrap;
				margin-bottom: 40rpx;
				padding: 0 46rpx;

				.item {
					width: 310rpx;
					margin-top: 22rpx;
					border-radius: 16px;
					background-color: #FFFFFF;
					padding: 4rpx;
					overflow: hidden;

					.items_main_img {
						width: 100%;
						height: 228rpx;
					}

					.item_body {
						padding: 14rpx 12rpx;

						.describe {
							display: flex;
							align-items: flex-start;

							.portrait {
								width: 54rpx;
								height: 54rpx;
								border-radius: 50%;
								margin-right: 12rpx;
							}

							.name {
								display: flex;
								flex-direction: column;
								justify-content: space-between;

								.shopName {
									font-size: 20rpx;
									font-weight: 600;
									color: #666666;
									line-height: 28rpx;
								}

								.tradeName {
									font-size: 22rpx;
									font-weight: 600;
									color: #333333;
									line-height: 32rpx;
								}
							}
						}

						.price {
							font-size: 22rpx;
							font-weight: 600;
							color: #EF4361;
							line-height: 42rpx;
							letter-spacing: 1rpx;
						}
					}
				}
			}
		}

		.contact_we {
			position: fixed;
			right: 24rpx;
			bottom: 150rpx;

			>image {
				width: 210rpx;
				height: 82rpx;
			}
		}
	}
</style>
