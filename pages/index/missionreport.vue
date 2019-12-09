<template>
	<view>
		<QSTabs :current="currentTab" line2Style="tab-line1" defaultColor="#888" activeColor="#D13D43" :tabs="tabList" width="187.5"
		 @change="tabChange" />
		<button @click="choose">选择视频</button>
	</view>

</template>

<script>
	import QSTabs from '@/components/QS-tabs/QS-tabs.vue';
	var _self;
	export default {
		data() {
			const token = '';

			return {
				token: '',
				currentTab: 0,
				news: [{
					NEWS_ID: '1234',
					TITLE: '条目测试条目测试条目测试条目测试条目测试条目测试条目测试',
					PUBLISH_DATE: '发布时间2019-19-12'
				}, {
					NEWS_ID: '1234',
					TITLE: '条目测试条目测试条目测试条目测试条目测试条目测试条目测试',
					PUBLISH_DATE: '发布时间2019-19-12'
				}, {
					NEWS_ID: '1234',
					TITLE: '条目测试条目测试条目测试条目测试条目测试条目测试条目测试',
					PUBLISH_DATE: '发布时间2019-19-12'
				}, {
					NEWS_ID: '1234',
					TITLE: '条目测试条目测试条目测试条目测试条目测试条目测试条目测试',
					PUBLISH_DATE: '发布时间2019-19-12'
				}],
				tabList: [{
					name: '待上报',
					value: '待上报'
				}, {
					name: '已上报',
					value: '已上报'
				}, {
					name: '待审核',
					value: '待审核'
				}, {
					name: '已审核',
					value: '已审核'
				}],
			};
		},
		methods: {
			tabChange(index) {
				_self.currentTab = index;
				console.log(_self.tabList[_self.currentTab].value)
			},
			choose() {
				uni.chooseVideo({
					count: 1,
					sourceType: ['camera', 'album'],
					success(res) {
						console.log(res)
					},
					fail(e) {
						console.log(e)
					}
				});
			}
		},
		onLoad() {
			_self = this;
			uni.getStorage({
				key: 'token',
				success: res => {
					_self.token = res.data;
				}
			});
		},
		onUnload() {},
		onShow() {},
		components: {
			QSTabs
		}
	};
</script>

<style>
	.body {
		display: flex;
		flex-direction: column;
		justify-content: center;
		text-align: center;
		align-items: center;
		padding-top: 50%;
	}

	.tab-line1 {
		background: #007AFF;
	}
</style>
