<template>
	<view class="home">
		<view class="wap-nav-bar">
			<view class="left">
				<image src="../../static/logo.png" mode=""></image>
				<view class="logo-dot"></view>
				<view class="logo-text">
					学历认证
				</view>
			</view>
			<view class="right" @click="open">
				<image src="../../static/1717949391295(1).png" mode=""></image>
			</view>
		</view>
		<view class="bg-white">
			<view class="left">
				<text>报告语种</text>
				<view class="tt">
					中文
				</view>
			</view>
			<view @click="down" class="right">
				<image src="../../static/1717949979221.png" mode=""></image>
			</view>
		</view>
		<view class="cont">
			<view class="title">
				中国高等教育学历认证报告
			</view>
			<view class="item">
				<view class="left">
					姓名
				</view>
				<view class="right">
					薛玉龙
				</view>
			</view>
			<view class="item">
				<view class="left">
					性别
				</view>
				<view class="right">
					男
				</view>
			</view>
			<view class="item">
				<view class="left">
					出生日期
				</view>
				<view class="right">
					1989年11月28日
				</view>
			</view>
			<view class="item">
				<view class="left">
					学历类型
				</view>
				<view class="right">
					普通
				</view>
			</view>
			<view class="item">
				<view class="left">
					层次
				</view>
				<view class="right">
					专科
				</view>
			</view>
			<view class="item">
				<view class="left">
					院校名称
				</view>
				<view class="right">
					北京长城研修学院
				</view>
			</view>
			<view class="item">
				<view class="left">
					专业名称
				</view>
				<view class="right">
					人力资源管理
				</view>
			</view>
			<view class="item">
				<view class="left">
					学制
				</view>
				<view class="right">
					三年
				</view>
			</view>
			<view class="item">
				<view class="left">
					入学日期
				</view>
				<view class="right">
					2016年09月
				</view>
			</view>
			<view class="item">
				<view class="left">
					毕业日期
				</view>
				<view class="right">
					2019年06月
				</view>
			</view>
			<view class="item">
				<view class="left">
					毕结业
				</view>
				<view class="right">
					毕业
				</view>
			</view>
			<view class="item">
				<view class="left">
					证书编号
				</view>
				<view class="right">
					110158201906035963
				</view>
			</view>
			<view class="item">
				<view class="left">
					报告编号
				</view>
				<view class="right">
					12135067
				</view>
			</view>
			<view class="item">
				<view class="left">
					打印日期
				</view>
				<view class="right">
					2022-09-27
				</view>
			</view>
		</view>
		<view class="bg-box">
			以上学历情况属实，专此认证
			<image src="../../static/1717982921834.png" mode=""></image>
		</view>
		<view class="items">
			<view class="left">
				毕业证书
			</view>
			<view class="right" @tap="_previewImage">
				<image class="x1" :src="imgs" mode=""></image>
				<image class="x2" src="../../static/1717983422554(1).png" mode=""></image>
			</view>
		</view>
		<view class="fot">
			<view class="">	
	主办单位：教育部学生服务与素质发展中心
			</view>
			<view class="x12">
	Copyright © 2003-2024 学信网  All Rights Reserved
			</view>
		</view>
		<uni-popup ref="popup" type="bottom" border-radius="10px 10px 0 0">
			<view class="pop">
				<view class="wap-nav-barx">
					<view class="left">
						<image src="../../static/logo.png" mode=""></image>
					</view>
					<view class="right" @click="close">
						<image src="../../static/1717986505914.png" mode=""></image>
					</view>
				</view>
				<view class="list">
					<view v-for="(item, index) in list" :key="index" class="list-item">
						{{item}}
					</view>
				</view>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	import UniPopup from '../../uni_modules/uni-popup/components/uni-popup/uni-popup.vue'
  export default {
    data() {
      return {
        imgs: require('../../static/b0f8aadee8c59f928e8d9f539ae37d9.jpg'),
		list: [
			'首页',
			'学籍查询',
			'学历查询',
			'学位查询',
			'在线验证',
			'出国教育背景...',
			'图像校对',
			'学信档案',
			'高考',
			'研招',
			'港澳台招生',
			'征兵',
			'就业',
			'学职平台'
		]
      }
    },
    onLoad() {
    },
    methods: {
		_previewImage() {
			//预览图片
			uni.previewImage({
				urls: [this.imgs],
				current: 0,
			})
		},
		down() {
			var oA = document.createElement("a");
			oA.download = ''; // 设置下载的文件名，默认是'下载'
			oA.href = this.imgs;
			document.body.appendChild(oA);
			oA.click();
			oA.remove(); // 下载之后把创建的元素删

		},
		open(){
		        // 通过组件定义的ref调用uni-popup方法 ,如果传入参数 ，type 属性将失效 ，仅支持 ['top','left','bottom','right','center']
		        this.$refs.popup.open('top')
		      },
		close () {
			this.$refs.popup.close()
		}
    }
  }
</script>

<style scoped lang="scss">
	.pop {
		padding: 30rpx;
		background: #fff;
		.wap-nav-barx {
			width: 100%;
		    display: flex;
		    align-items: center;
		    background: #fff;
			  display: flex;
			  align-items: center;
			  justify-content: space-between;
			  .left {
				  display: flex;
				  align-items: center;
				  image {
					  width: 172rpx;
					  height: 48rpx;
				  }
			  }
			  .right {
				  margin-right: 30rpx;
				  image {
					  width: 40rpx;
					  height: 44rpx;
				  }
			  }
		}
		.list {
			display: flex;
			align-items: center;
			flex-wrap: wrap;
			.list-item {
				margin-top: 30rpx;
				width: 30%;
				height: 60rpx;
				border-radius: 4rpx;
				background: rgb(245, 245, 245);
				font-size: 28rpx;
				overflow:hidden; //超出的文本隐藏
				text-overflow:ellipsis; //溢出用省略号显示
				white-space:nowrap; //溢出不换行
				text-align: center;
				line-height: 60rpx;
			}
			.list-item:nth-of-type(2) {
				margin-left: 4%;
			}
			.list-item:nth-of-type(3) {
				margin-left: 4%;
			}
			.list-item:nth-of-type(5) {
				margin-left: 4%;
			}
			.list-item:nth-of-type(6) {
				margin-left: 4%;
			}
			.list-item:nth-of-type(8) {
				margin-left: 4%;
			}
			.list-item:nth-of-type(9) {
				margin-left: 4%;
			}
			.list-item:nth-of-type(11) {
				margin-left: 4%;
			}
			.list-item:nth-of-type(12) {
				margin-left: 4%;
			}
			.list-item:nth-of-type(14) {
				margin-left: 4%;
			}
		}
	}
  .home {
	  width: 100%;
	  height: 100vh;
	  overflow-y: scroll;
	  background: #fff;
  }
  .wap-nav-bar {
      position: relative;
      z-index: 1;
	  width: 100%;
      height: 98rpx;
      display: flex;
      align-items: center;
      background: #fff;
      border-bottom: 2rpx solid #E8EAED;
	  display: flex;
	  align-items: center;
	  justify-content: space-between;
	  .left {
		  padding-left: 30rpx;
		  display: flex;
		  align-items: center;
		  image {
			  width: 172rpx;
			  height: 48rpx;
		  }
		  .logo-dot {
			  width: 2rpx;
			  height: 44rpx;
			  background: #E8EAED;
				margin: 0 20rpx;
		  }
		  .logo-text {
			  color: #60656E;
		  }
	  }
	  .right {
		  margin-right: 30rpx;
		  image {
			  width: 44rpx;
			  height: 44rpx;
		  }
	  }
  }
	.bg-white {
		padding: 30rpx;
		font-size: 28rpx;
		display: flex;
		justify-content: space-between;
		.left {
			display: flex;
			align-items: center;
			font-size: 24rpx;
			.tt {
				margin-left: 24rpx;
				background: rgb(239 ,248, 249);
				    color: #00bac7;
					width: 70rpx;
					height: 50rpx;
					text-align: center;
					line-height: 50rpx;
					border-radius: 4rpx;
			}
		}
		.right {
			image {
				width: 42rpx;
				height: 42rpx;
			}
		}
	}
	.cont {
		.title {
			padding-top: 10rpx;
			font-weight: 600;
			font-size: 40rpx;
			text-align: center;
			margin-bottom: 30rpx;
		}
		.item {
			padding-top: 24rpx;  
			display: flex;
			font-size: 30rpx;
			.left {
				width: 33%;
				color: #889098;
				text-align: right;
				padding-right: 24rpx;
			}
			.right {
				width: 66%;
			}
		}
	}
	.bg-box {
		margin-top: 70rpx;
		height: 112rpx;
		width: 100%;
		background: url('../../static/zcrz-bg.png') no-repeat;
		background-size: 100% 100%;
		color: #fff;
		font-weight: 700;
		display: flex;
		align-items: center;
		justify-content: center;
		image {
			width: 40rpx;
			height: 42rpx;
			margin-left: 24rpx;
		}
	}
	.items {
		padding-top: 60rpx;  
		display: flex;
		align-items: center;
		font-size: 30rpx;
		.left {
			width: 33%;
			color: #889098;
			text-align: right;
			padding-right: 24rpx;
		}
		.right {
			width: 66%;
			display: flex;
			align-items: center;
			justify-content: space-between;
			.x1 {
				width: 132rpx;
				height: 88rpx;
			}
			.x2 {
				margin-right: 48rpx;
				width: 26rpx;
				height: 30rpx;
			}
		}
	}
	.fot {
		font-size: 26rpx;
		margin-top: 60rpx;
		  display: flex;
		  align-items: center;
		  flex-direction: column;
		  justify-content: center;
		height: 150rpx;
		width: 100%;
		background: rgb(40, 40, 40);
		color: #969696;
		.x12 {
			margin-top: 12rpx;
		}
	}
</style>
