<template>
	<view class="content">
		<view class="banner">
			<view class="banner_img" @click="aboutClosed = true">
				<image src="/static/images/banner.png" mode=""></image>
			</view>
			<view class="banner_about todaysDealTitle" v-if="aboutClosed">
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
		<!-- 固定栏 -->
		<view :class="[{fixedTop:hightTop},'todaysDeal']">
			<!-- 标题 -->
			<view class="customNavigation"
				:style="{ paddingTop: top+ 'px',lineHeight: height+ 'px',paddingBottom:'10rpx'  }"
				v-if="wmssjH5 < scrollTop">
				S石材推荐
			</view>
			<!-- 一级菜单 -->
			<view class="one_tabs no-scrollbar" v-if="wmssjH1  < scrollTop">
				<view class="one_tab_item" :style="{fontWeight: actice == key ? 600 : ''}"
					v-for="(iten,key) in moduleList" :key="key" @click="tabOneClick(iten,key)">
					{{ iten.tabName }}
				</view>
				<view class="underline" :style="{ left: (actice === 0 ? actice*150 :  actice*(150+120)) + 'rpx'  }">
				</view>
			</view>
			<view class="tabs">
				<!-- 二三级菜单 -->
				<view v-if="wmssjH4 < scrollTop">
					<view class="two_tabs no-scrollbar">
						<view :class="[{actice:moduleList[2].actice1 == index1},'two_tab_item']"
							v-for="(item1,index1) in moduleList[2].tabs1" :key="index1"
							@click="tabTwoClick(moduleList[2],item1,index1)">
							{{ item1 }}
						</view>
					</view>
					<view class="three_tabs no-scrollbar">
						<view :class=" [{actice:moduleList[2].actice2==index2},'three_tab_item']"
							v-for="(item2,index2) in moduleList[2].tabs2" :key="index2"
							@click="tabThreeClick(moduleList[2],item2,index2)">
							{{ item2 }}
						</view>
					</view>
				</view>
				<view v-else-if="wmssjH3 < scrollTop">
					<view class="two_tabs no-scrollbar">
						<view :class="[{actice:moduleList[1].actice1 == index1},'two_tab_item']"
							v-for="(item1,index1) in moduleList[1].tabs1" :key="index1"
							@click="tabTwoClick(moduleList[1],item1,index1)">
							{{ item1 }}
						</view>
					</view>
					<view class="three_tabs no-scrollbar">
						<view :class=" [{actice:moduleList[1].actice2==index2},'three_tab_item']"
							v-for="(item2,index2) in moduleList[1].tabs2" :key="index2"
							@click="tabThreeClick(moduleList[1],item2,index2)">
							{{ item2 }}
						</view>
					</view>
				</view>
				<view v-else-if="wmssjH2 < scrollTop">
					<view class="two_tabs no-scrollbar">
						<view :class="[{actice:moduleList[0].actice1 == index1},'two_tab_item']"
							v-for="(item1,index1) in moduleList[0].tabs1" :key="index1"
							@click="tabTwoClick(moduleList[0],item1,index1)">
							{{ item1 }}
						</view>
					</view>
					<view class="three_tabs no-scrollbar">
						<view :class=" [{actice:moduleList[0].actice2==index2},'three_tab_item']"
							v-for="(item2,index2) in moduleList[0].tabs2" :key="index2"
							@click="tabThreeClick(moduleList[0],item2,index2)">
							{{ item2 }}
						</view>
					</view>
				</view>
			</view>
		</view>
		<!-- 固定栏 -->
		<!-- 页面一级菜单 -->
		<view class="tabs_main">
			<view class="tabs todaysDealTabs">
				<view class="one_tabs no-scrollbar">
					<view class="one_tab_item" :style="{fontWeight: actice == key ? 600 : ''}"
						v-for="(iten,key) in moduleList" :key="key" @click="tabOneClick(iten,key)">
						{{ iten.tabName }}
					</view>
					<view class="underline" :style="{ left: (actice === 0 ? actice*150 :  actice*(150+120)) + 'rpx'  }">
					</view>
				</view>
			</view>
		</view>
		<!-- 页面一级菜单 -->
		
		<view class="tabs_main" v-for="(item,index) in moduleList" :key="index">
			<!-- 页面二三级菜单 -->
			<view class="tabs">
				<view class="small_banner">
					<image src="../../static/images/small_banner.png" mode=""></image>
				</view>
				<view class="two_tabs no-scrollbar">
					<view :class="[{actice:item.actice1 == index1},'two_tab_item']" v-for="(item1,index1) in item.tabs1"
						:key="index1" @click="tabTwoClick(item,item1,index1)">
						{{ item1 }}
					</view>
				</view>
				<view class="three_tabs no-scrollbar">
					<view :class=" [{actice:item.actice2==index2},'three_tab_item']"
						v-for="(item2,index2) in item.tabs2" :key="index2" @click="tabThreeClick(item,item2,index2)">
						{{ item2 }}
					</view>
				</view>
			</view>
			<!-- 页面二三级菜单 -->
			<!-- 列表 -->
			<view :class="[`todaysDeal${index}`,'main_items']">
				<view class="item" v-for="(item,index) in item.list" :key="index">
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
			<!-- 列表 -->
			<view class="more">
				查看更多石材
			</view>

		</view>
		<view class="contact_we" v-if="isEnterStore">
			<image src="../../static/images/enterStore.png" mode=""></image>
		</view>
		<view class="contact_we" v-else>
			<image src="../../static/images/contact.png" mode=""></image>
			<button class="contact" open-type="contact"></button>
		</view>
	</view>
</template>

<script>
	import {
		module
	} from '../../static/js/index.js'
	export default {
		data() {
			return {
				text: [
					'一、 石材:是指从沉积岩、岩浆岩、变质岩的天然岩体中开采的岩石。',
					'二、天然石材大体分为花岗岩、板岩、砂岩、石灰岩、火山岩等，随着科技的不断发展和进步，人造石的产品也不断日新月异石材早已经成为建筑、装饰、道路、桥梁建设的重要原料之一。'
				],
				aboutClosed: true,
				moduleList: [],
				actice: 0,
				wmssjH1: 0,
				wmssjH2: 0,
				wmssjH3: 0,
				wmssjH4: 0,
				wmssjH5: 0,
				hightTop: false,
				height: 0,
				top: 0,
				scrollTop: 0,
				isEnterStore: false
			}
		},
		async onReachBottom() {
			console.log("onReachBottom");
		},
		onLoad() {
			this.moduleList = module
		},
		onPageScroll: function(e) { //监听页面滚动
			let that = this
			that.scrollTop = e.scrollTop
			//判断你滑动的高度大于你元素距离顶部的高度值
			if (that.wmssjH5 < e.scrollTop) {
				//固定
				that.hightTop = true
				if (that.wmssjH4 < e.scrollTop) {
					that.actice = 2
				} else if (that.wmssjH3 < e.scrollTop) {
					that.actice = 1
				} else if (that.wmssjH2 < e.scrollTop) {
					that.actice = 0
				}
				console.log(that.actice)
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
			query.select('.todaysDealTabs').boundingClientRect(data => {
				//data.top获取距离顶部的值
				this.wmssjH1 = data.top - this.top - this.height - 5
			}).exec()
			const query1 = uni.createSelectorQuery().in(this);
			query1.select('.todaysDeal0').boundingClientRect(data => {
				//data.top获取距离顶部的值
				this.wmssjH2 = data.top - this.top - this.height - 55
			}).exec()
			const query2 = uni.createSelectorQuery().in(this);
			query2.select('.todaysDeal1').boundingClientRect(data => {
				//data.top获取距离顶部的值
				this.wmssjH3 = data.top - this.top - this.height - 138
			}).exec()
			const query3 = uni.createSelectorQuery().in(this);
			query3.select('.todaysDeal2').boundingClientRect(data => {
				//data.top获取距离顶部的值
				this.wmssjH4 = data.top - this.top - this.height - 138
			}).exec()
			const query4 = uni.createSelectorQuery().in(this);
			query4.select('.todaysDealTitle').boundingClientRect(data => {
				//data.top获取距离顶部的值
				this.wmssjH5 = data.top
			}).exec()

		},
		methods: {
			tabOneClick(row, index) {
				let scrollTop = 0
				switch (index) {
					case 0:
						scrollTop = this.wmssjH2 + 5
						break;
					case 1:
						scrollTop = this.wmssjH3 + 5
						break;
					case 2:
						scrollTop = this.wmssjH4 + 5
						break;
				}
				uni.pageScrollTo({
					scrollTop,
					duration: 300
				});
			},
			tabTwoClick(row, row1, index) {
				row.actice1 = index
			},
			tabThreeClick(row, row1, index) {
				row.actice2 = index
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

		.todaysDeal {
			.customNavigation {
				text-align: center;
				font-size: 30rpx;
				font-weight: 600;
				color: #FFFFFF;
				line-height: 42rpx;
			}

			.one_tabs {
				position: relative;
				width: 704rpx;
				overflow-x: auto;
				display: flex;
				align-items: center;
				margin-left: 46rpx;

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

			.tabs {
				padding: 0 46rpx;

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

		.tabs_main {
			color: #FFF;

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

		.more {
			width: 658rpx;
			height: 96rpx;
			line-height: 96rpx;
			border-radius: 16rpx;
			border: 2rpx solid #FFFFFF;
			margin: 0 auto 72rpx;
			text-align: center;
		}

		.contact_we {
			position: fixed;
			right: 24rpx;
			bottom: 150rpx;

			>image {
				width: 210rpx;
				height: 82rpx;
			}

			.contact {
				position: absolute;
				top: 0;
				left: 0;
				width: 100%;
				height: 100%;
				opacity: 0;
			}
		}
	}
</style>
