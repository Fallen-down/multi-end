<template>
	<view class="container">
		<u-search class="search" :style="{'margin-top':statusBarHeight + 'px'}" shape="round" :clearabled="true" :show-action="false"
		 placeholder="" v-model="keyword"></u-search>
		<view class="wrap">
			<u-swiper :list="bannerList"></u-swiper>
		</view>
		<u-grid :col="3">
			<u-grid-item>
				<u-icon name="photo" :size="46"></u-icon>
				<view class="grid-text">图片</view>
			</u-grid-item>
			<u-grid-item>
				<u-icon name="lock" :size="46"></u-icon>
				<view class="grid-text">锁头</view>
			</u-grid-item>
			<u-grid-item>
				<u-icon name="hourglass" :size="46"></u-icon>
				<view class="grid-text">沙漏</view>
			</u-grid-item>
		</u-grid>
		<uni-list>
			<uni-list-item title="精选咨询" link="reLaunch" to="/pages/vue/index/index" @click="onClick($event,1)"></uni-list-item>
		</uni-list>
		<view class="text-area">
			<text class="title">{{title}}</text>
			<u-action-sheet :list="list" v-model="show"></u-action-sheet>
		</view>
		<u-icon name="check-circle" custom-prefix="custom-icon" size="30" color="#f8f"></u-icon>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				statusBarHeight: '',
				title: 'Hello',
				list: [{
					text: '点赞',
					color: 'blue',
					fontSize: 28
				}, {
					text: '分享'
				}, {
					text: '评论'
				}],
				show: false,
				keyword: '',
				bannerList: [{
						image: 'https://cdn.uviewui.com/uview/swiper/1.jpg',
						title: '昨夜星辰昨夜风，画楼西畔桂堂东'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/2.jpg',
						title: '身无彩凤双飞翼，心有灵犀一点通'
					},
					{
						image: 'https://cdn.uviewui.com/uview/swiper/3.jpg',
						title: '谁念西风独自凉，萧萧黄叶闭疏窗，沉思往事立残阳'
					}
				],
			}
		},
		onLoad() {
			const res = uni.getSystemInfoSync();
			this.statusBarHeight = res.statusBarHeight;

			this.$u.api.getInfo({
				username: 'test',
				password: '123',

			}, {
				serviceName: 'LoginService'
			}).then(res => {
				console.log(res);
			}).catch(error => {
				console.log(error);
			})
		},
		methods: {
			onClick() {},
			modifyVuex() {
				this.$u.vuex('vuex_version', '1.0.1');
				this.$u.vuex('vuex_user.name', '诗圣');
			}
		}
	}
</script>

<style lang="scss">
	.search {
		margin-bottom: 1em;
	}

	.wrap {
		padding: 40rpx;
	}
</style>
