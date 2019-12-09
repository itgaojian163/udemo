<template>
	<view class="conbox">
		<view class="container">
			<!-- 背景 -->
			<image src="../../static/img/bg.png" class="cont" mode=""></image>
			<view class="canvas-content">
				<view class="title">身份认证</view>
				<view class="login-form">
					<view class="item">
						<image class="icon left" src="/static/icon_phone.png" mode="widthFix"></image>
						<input style="width: 85%;" class="uni-input" focus placeholder="请输入姓名" placeholder-class="input-placeholder" />
					</view>
					<view class="item">
						<image class="icon left" src="/static/icon_id_card.png" mode="widthFix"></image>
						<input style="width: 85%;" class="uni-input" placeholder="请输入身份证号码" placeholder-class="input-placeholder" />
					</view>
					<view class="btn">
						<text>身份认证</text>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {
			register() {
				uni.navigateTo({
					url: 'missionplan'
				})
			}
		}
	}
</script>
<style scoped>
	.conbox {
		width: 750rpx;
		height: 100vh;
		overflow-x: hidden;
		overflow-y: scroll;
	}

	.container,
	image.cont {
		width: 750rpx;
		min-height: 100vh;
		height: auto;
		position: relative;
	}

	image.cont {
		height: 100%;
		position: absolute;
		z-index: 0;
	}

	image.caidai {
		position: absolute;
		top: 0;
		left: 0;
		width: 750rpx;
		height: 1024rpx;
	}

	.header {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		/* height: 246rpx; */
		padding-top: 48rpx;
		padding-bottom: 40rpx;
		box-sizing: border-box;
		position: relative;
		z-index: 3;
	}

	.header-title {
		width: 100%;
		height: 60rpx;
		display: flex;
		align-items: center;
		padding: 0 48rpx;
		box-sizing: border-box;
		justify-content: space-between;
	}

	.header-title>view {
		padding: 8rpx 16rpx;
		border: 1px solid #d89720;
		color: #d89720;
		font-size: 28rpx;
		border-radius: 26rpx;
	}

	/* 转盘 */
	.canvas-container {
		margin: 0 auto;
		position: relative;
		top: 300rpx;
		width: 600rpx;
		height: 600rpx;
		background: #007AFF;
		background-size: cover;
	}

	.canvas {
		width: 100%;
		height: 100%;
		display: block !important;
		border-radius: 50%;
	}

	.canvas-content {
		margin: 0 auto;
		position: relative;
		display: flex;
		top: 350rpx;
		padding: 20rpx;
		justify-content: center;
		flex-direction: column;
		width: 80%;
		height: 600rpx;
		background: #fff;
		border-radius: 2%;
		box-shadow: 10rpx 10rpx 40rpx #F8F8F8;
		background-size: cover;
		/* background-clip: padding-box; */
		/* background-color: #ffcb3f; */
	}

	.canvas-element {
		position: relative;
		z-index: 1;
		width: inherit;
		height: inherit;
		border-radius: 50%;
	}

	.canvas-list {
		position: absolute;
		left: 0;
		top: 0;
		width: inherit;
		height: inherit;
		z-index: 9999;
	}

	.canvas-item {
		position: absolute;
		left: 0;
		top: 0;
		width: 100%;
		height: 100%;
		color: #e4370e;
		/* text-shadow: 0 1rpx 1rpx rgba(255, 255, 255, 0.6); */
	}

	.canvas-item-text {
		position: relative;
		display: block;
		padding-top: 46rpx;
		margin: 0 auto;
		text-align: center;
		-webkit-transform-origin: 50% 300rpx;
		transform-origin: 50% 300rpx;
		display: flex;
		flex-direction: column;
		align-items: center;
		color: #FB778B;
	}

	.canvas-item-text text {
		font-size: 30rpx;
	}

	.canvas-item-text-img {
		width: 50rpx;
		height: 50rpx;
		padding-top: 30rpx;
	}

	/* 分隔线 */
	.canvas-line {
		position: absolute;
		left: 0;
		top: 0;
		width: inherit;
		height: inherit;
		z-index: 99;
	}

	.canvas-litem {
		position: absolute;
		left: 300rpx;
		top: 0;
		width: 3rpx;
		height: 300rpx;
		background-color: rgba(228, 55, 14, 0.4);
		overflow: hidden;
		-webkit-transform-origin: 50% 300rpx;
		transform-origin: 50% 300rpx;
	}

	/**  
* 抽奖按钮  
*/
	.canvas-btn {
		position: absolute;
		left: 260rpx;
		top: 260rpx;
		z-index: 400;
		width: 80rpx;
		height: 80rpx;
		border-radius: 50%;
		color: #f4e9cc;
		background-color: #e44025;
		line-height: 80rpx;
		text-align: center;
		font-size: 26rpx;
		text-shadow: 0 -1px 1px rgba(0, 0, 0, 0.6);
		box-shadow: 0 3px 5px rgba(0, 0, 0, 0.6);
		text-decoration: none;
	}

	.canvas-btn::after {
		position: absolute;
		display: block;
		content: ' ';
		left: 12rpx;
		top: -44rpx;
		width: 0;
		height: 0;
		overflow: hidden;
		border-width: 30rpx;
		border-style: solid;
		border-color: transparent;
		border-bottom-color: #e44025;
	}

	.canvas-btn.disabled {
		pointer-events: none;
		background: #b07a7b;
		color: #ccc;
	}

	.canvas-btn.disabled::after {
		border-bottom-color: #b07a7b;
	}

	.canvas-btn-table {
		color: #A83FDB;
		width: 120rpx;
		text-align: center;
		position: absolute;
		left: 240rpx;
		top: 360rpx;
		font-size: 26rpx;
		background-color: #FFFFFF;
		opacity: 0.9;
	}

	.typecheckbox {
		width: 100%;
		position: relative;
		z-index: 3;
		display: flex;
		justify-content: space-between;
		padding: 20rpx;
		box-sizing: border-box;
		color: #fff;
		font-size: 28rpx;
		top: -120rpx;
		flex-direction: column;
		height: 180rpx;
		align-items: flex-end;
		/* padding-top: 46rpx; */
	}

	.typecheckbox view {
		border: 1px solid #FF3637;
		background: transparent;
		color: #FF3637;
		display: flex;
		height: 60rpx;
		width: 140rpx;
		border-radius: 50rpx;
		align-items: center;
		justify-content: center;
		display: flex;
		margin-left: 20rpx;
	}

	.typecheckbox view.active {
		background: #FF3637;
		color: #fff;
	}

	.guize {
		width: 502rpx;
		min-height: 300rpx;
		display: flex;
		flex-direction: column;
		position: relative;
		z-index: 3;
		background-image: linear-gradient(-180deg, #F48549 0%, #F2642E 100%);
		border: 18rpx solid #E4431A;
		border-radius: 16px;
		margin: 0 auto;
		margin-top: -104rpx;
		padding: 48rpx;
		/* box-sizing: border-box; */
		color: #fff;
	}

	.guize .title {
		text-align: center;
		margin-bottom: 28rpx;
	}

	.guize .g_item {
		font-family: PingFang-SC-Medium;
		font-size: 24rpx;
		color: #FFFFFF;
		letter-spacing: 0.5px;
		text-align: justify;
		line-height: 20px;
	}

	.shadowbox {
		width: 750rpx;
		height: 100vh;
		position: fixed;
		top: 0;
		left: 0;
		z-index: 999;
		background: rgba(0, 0, 0, .6);
		display: flex;
		justify-content: center;
		align-items: center;

	}

	.myrewards {
		width: 600rpx;
		min-height: 80rpx;
		background: #FFEEDF;
		border: 10rpx solid #F2692F;
		color: #333;
		font-size: 24rpx;
		font-family: PingFang-SC-Medium;
		border-radius: 40rpx;
		padding-bottom: 20rpx;
	}

	.myrewards .title {
		font-family: PingFang-SC-Bold;
		font-size: 16px;
		color: #E4431A;
		letter-spacing: 0.57px;
		display: flex;
		padding-top: 36rpx;
		justify-content: center;
	}

	.myrewards .itembox {

		max-height: 320rpx;
		overflow-y: auto;
	}

	.myrewards .item {
		width: 70%;
		height: 66rpx;
		padding: 0 32rpx;
		box-sizing: border-box;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}

	.login-form {
		width: 100%;
		margin: 40rpx auto;
		min-height: auto;
		height: 500rpx;
	}

	.login-form .item {
		width: 100%;
		height: 84rpx;
		border-radius: 6rpx;
		margin-bottom: 33rpx;
		display: flex;
		justify-content: space-around;
		align-items: center;
		background-color: #ffffff;
		border: 1px solid #C0C0C0;
		border-radius: 10rpx;
	}

	.login-form input {
		color: #C0C0C0;
		height: 84rpx;
		font-size: 25rpx;
		line-height: 84rpx;
	}

	.login-form .item .icon {
		width: 40rpx;
		height: 40rpx;
	}

	.input-placeholder {
		color: #C0C0C0;
		line-height: 84rpx;
		height: 84rpx;
		margin: auto;
	}

	.login-form .btn {
		margin: 43rpx auto 22rpx auto;
		text-align: center;
		height: 84rpx;
		width: 95%;
		line-height: 84rpx;
		border-radius: 15rpx;
		font-size: 30rpx;
		color: #FFFFFF;
		background-color: #FF0000;
	}

	.login-form .btn:active {
		margin: 43rpx auto 22rpx auto;
		text-align: center;
		height: 84rpx;
		width: 95%;
		line-height: 84rpx;
		border-radius: 15rpx;
		color: #000000;
		background-color: #FFEEDF;
	}

	.forgot-pwd {
		text-align: right;
	}

	.login-third .text {
		margin: 137rpx auto 106rpx auto;
		text-align: center;
	}

	.login-third .flex {
		text-align: center;
		display: flex;
		justify-content: space-around;
	}

	.login-third .flex image {
		width: 88rpx;
		height: 88rpx;
	}

	.canvas-content .title {
		color: #FF0000;
		font-weight: bold;
	}

	.hint-bottom {
		font-size: 25rpx;
		color: #555555;
	}

	.register {
		color: #FF0000;
		text-decoration: underline;
	}

	/* text {
		height: 30rpx;
		font-family: PingFang-SC-Regular;
		font-size: 32rpx;
		font-weight: bold;
		font-stretch: normal;
		line-height: 40rpx;
		letter-spacing: 3rpx;
		color: #ffffff;
	} */
</style>
