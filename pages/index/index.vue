<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<navigator url="/pages/list/list">点击list</navigator>
		<navigator url="/subpkg/news/news">点击news</navigator>
		<button @click="choseImg">点击获取照片</button>
		<image :src="imgSrc"></image>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				imgSrc:''
			}
		},
		onLoad() {

		},
		methods: {
			choseImg(){
				uni.chooseImage({
					count:1,
					sizeType:['orginal','compressed'],
					sourceType:['album','camera'],
					success:(res)=> { //注意写成箭头函数 不然获取不到this
						console.log(this);
						this.imgSrc = res.tempFilePaths[0];
						console.log(this.imgSrc);
					}
				})
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
