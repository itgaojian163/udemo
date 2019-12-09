<template>
	<view style="display: flex;flex-direction: column;">
		<view class="header-box">
			<scroll-view scroll-x="true" class="header-tabs">
				<view class="tab-items">
					<view v-for="(header,index) in headerTabs" :key="index" @click="getCurrentTab(header,index)">
						<view v-if="index===headerTabs.length-1">
							{{header.name}}
						</view>
						<view v-else>
							{{header.name+' >> '}}
						</view>
					</view>
				</view>
			</scroll-view>
			<view class="divider"></view>
		</view>

		<view class="container-box">
			<view v-for="(item,index) in currentData" :key="index">
				<view class="item-box">
					<view class="item-content">
						<view class="item-org-name" @click="selectTreeItem(item,index)">{{item.name}}</view>
						<view>
							<checkbox :checked="item.isCheck" @click="checkItem($event,item,index)"></checkbox>
						</view>
					</view>
					<view class="divider"></view>
				</view>
			</view>
		</view>
		<view class="btn-box">
			<button class="btn" @click="confirmChoose">确定</button>
		</view>
	</view>
</template>

<script>
	import treeBean from '../../common/tree.js'
	var _self;
	export default {
		data() {
			const token = '';
			return {
				token: '',
				treeData: [],
				selTreeData: [],
				selectTreeData: [],
				parent: [],
				currentData: [],
				chooseData: [],
				isMutil: true, //是否多选 true 可以多线 false 单选
				headerTabs: [{
					name: '卓资县组织部',
					value: '123'
				}]
			};
		},
		methods: {
			initTree(list) {
				for (var i = 0; i < list.length; i++) {
					list[i].isCheck = false
					if (list[i].subList != undefined && list[i].subList.length > 0) {
						_self.initTree(list[i].subList)
					} else {
						continue
					}
				}
			},
			selectTreeItem(item, index) {
				if (item.subList) {
					_self.currentData = item.subList
				}
			},
			getCurrentData(parent, root) {
				if (parent.length > 0) {
					_self.currentData = parent
				} else {
					_self.currentData = root
				}
			}
		},
		onLoad() {
			_self = this;
			_self.treeData = treeBean.list
			_self.initTree(_self.treeData)
			_self.getCurrentData(_self.parent, _self.treeData)
		},
		onUnload() {},
		onShow() {},
		components: {}
	};
</script>

<style>
	.header-box {
		position: fixed;
		flex-direction: column;
		width: 100%;
		background: #FFFFFF;
		z-index: 999;
	}

	.header-tabs {
		width: 100%;
		white-space: nowrap;
		position: relative;
	}

	.divider {
		background: #CCCCCC;
		width: 100%;
		white-space: nowrap;
		height: 1rpx;
	}

	.item-org-name {
		font-size: 25rpx;
		width: 70%;
	}

	.tab-items {
		display: flex;
		flex-direction: row;
		width: 100%;
		text-align: center;
		align-items: center;
		height: 80rpx;
		font-size: 50rpx;
		font-weight: bold;
		padding: 15rpx;
		margin-right: 20rpx;
	}

	.container-box {
		margin-bottom: 85rpx;
		margin-top: 120rpx;
	}

	.btn-box {
		width: 100%;
		position: fixed;
		bottom: 0upx;
	}

	.item-box {
		width: 100%;
		display: flex;
		flex-direction: column;
	}

	.item-content {
		padding: 20rpx;
		display: flex;
		font-size: 20rpx;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
	}

	.btn {
		width: 100%;
		line-height: 80rpx;
		margin-bottom: 5rpx;
		color: #FFFFFF;
		background: #FF0000;
	}
</style>
