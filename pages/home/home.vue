<template>
	<view class="content">
		<view id="box">
			<!-- <image class="bg-image" mode="scaleToFill" src="/static/bg.jpg"></image> -->
			<swiper indicator-color="white" autoplay interval="2000" circular>
				<swiper-item>
					<image src="/static/swiper/icon.png"></image>
				</swiper-item>
			</swiper>
		</view>
		<view class="title">Today's Schedule</view>
		<view class="center">
			<view class="center_top">
				<text>{{ newtime() }}</text>
				<text v-if="todayCour.length">今天一共{{ todayCour.length }}节课</text>
				<text>Week {{ week }}</text>
			</view>
		</view>
		<view class="title">Tool</view>
		<view class="top">
			<navigator url="/pages/schedule/schedule" class="ability">
				<text>Schedule</text>
				<image src="/static/tab/schedule.png"
					 />
			</navigator>
			<navigator url="/pages/map/map" class="ability">
				<text>Map</text>
				<image src="/static/tab/schedule.png"
					 />
			</navigator>
			<navigator url="/pages/about/about" class="ability">
				<text>About</text>
				<image src="/static/tab/user.png"
					 />
			</navigator>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				todayCour: [],
				week: 0,
				islogin: false,
				swiper: [
					'/static/swiper/icon.png',
					'/static/swiper/cdut.png',
					'/static/swiper/oxford.png'
				]
			};
		},
		onLoad() {},
		methods: {
			swierChange(e) {
				this.currentIndex = e.detail.current
			}
		}
	}
</script>

<style lang="scss">
	@keyframes animated-border {
		0% {
			box-shadow: 0 0 0 0 rgba(83, 232, 255, 0.4);
		}

		100% {
			box-shadow: 0 0 0 40rpx rgba(121, 255, 37, 0.0);
		}
	}

	#box {
		animation: animated-border 1.5s infinite;
	}
	.content {
		box-sizing: border-box;
		height: 100%;
		width: 100%;
		font-size: 28rpx;
		background-image: linear-gradient(208deg, #f3f3dc 10%, #cacaff 20%, #e0f8f8 50%);
	}
	
	.top {
		display: flex;
		justify-content: space-between;
		.ability {
			width: 31%;
			color: #191919;
			height: 268rpx;
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: space-around;
			border-radius: 28rpx;
			font-size: 28rpx;
			font-weight: bolder;
			letter-spacing: 4rpx;
			box-shadow: 9rpx 9rpx 10rpx #818181;
			&:nth-child(1) {
				background-color: #fcefe9;
			}
			&:nth-child(2) {
				background-color: #f0fdf5;
			}
			&:nth-child(3) {
				background-color: #ffe0ff;
			}
			image {
				height: 158rpx;
				width: 158rpx;
			}
			text {
				margin-top: 30rpx;
			}
		}
	}
	swiper {
		height: 300rpx;
	}

	swiper image {
		width: 100%;
		height: 100%;
	}

	.bg-image {
		width: 100%;
		height: 100%;
		position: fixed;
		z-index: -1;
	}

	.title {
		padding: 50rpx 35rpx 38rpx 35rpx;
		font-size: 32rpx;
		font-weight: bolder;
		color:gray;
		letter-spacing: 3rpx;
		position: relative;

		&::after {
			content: '';
			position: absolute;
			left: 13rpx;
			background-color: #2eeaf4;
			width: 12rpx;
			height: 33%;
			bottom: 37rpx;
			border-radius: 10rpx;
		}
	}

	.center {
		min-height: 300rpx;
		padding-top: 10rpx;
		border-radius: 38rpx;
		box-shadow: #ccc 8rpx 8rpx 8rpx;
		color: #191919;
		background-image: linear-gradient(0deg, #1aff62 20%, #f8f8f8 100%);

	}

	.center_top {
		padding: 2rpx 10rpx;

		text {
			margin: 0 28rpx;
			font-family: Arial;
			&:last-child {
				position: absolute;
				right: 18rpx;
			}
		}
	}
</style>
