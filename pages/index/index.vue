<template>
	<view class="container">
		<countdown-timer ref="countdown" :time="time" @finish="onFinish">
			
			<template v-slot="{day, hour, minute, second, remain, time}">
				<!-- 基本样式 -->
				<view class="case">
					<view class="title">基本：</view>
					<view>{{day}}天{{hour}}时{{minute}}分{{second}}秒</view>				
				</view>
				<!-- #ifndef MP -->
				<!-- 自定义样式 -->
				<view class="case">
					<view class="title">自定义样式：</view>
					<view class="custom">
						<view>{{fillWithZero(hour + (day * 24), 2)}}</view>
						<view>:</view>
						<view>{{fillWithZero(minute, 2)}}</view>
						<view>:</view>
						<view>{{fillWithZero(second, 2)}}</view>
					</view>
				</view>
				<!-- #endif -->
				<!-- 按最大有效单位显示 -->
				<view class="case">
					<view class="title">按最大有效单位显示：</view>
					<view>
						<text v-if="day > 0">{{day}}天</text>
						<text v-else-if="hour > 0">{{hour}}小时</text>
						<text v-else-if="minute > 0">{{minute}}分钟</text>
						<text v-else-if="second > 0">{{second}}秒</text>
						<text v-else>倒计时结束</text>
					</view>				
				</view>
				<!-- 剩余多少天 -->
				<view class="case">
					<view class="title">剩余多少天：</view>
					<view>{{day}}</view>				
				</view>
				<!-- 剩余多少小时 -->
				<view class="case">
					<view class="title">剩余多少小时：</view>
					<view>{{day * 24 + hour}}</view>				
				</view>
				<!-- 剩余多少分钟 -->
				<view class="case">
					<view class="title">剩余多少分钟：</view>
					<view>{{day * 1440 + hour * 60 + minute}}</view>				
				</view>
				<!-- 剩余多少秒 -->
				<view class="case">
					<view class="title">剩余多少秒：</view>
					<view>{{day * 86400 + hour * 3600 + minute * 60 + second}}</view>				
				</view>
				<!-- 剩余多少毫秒 -->
				<view class="case">
					<view class="title">剩余多少毫秒：</view>
					<view>{{remain + 1000}}</view>				
				</view>
				<!-- 过了多少秒 -->
				<view class="case">
					<view class="title">过了多少秒：</view>
					<view>{{(time - remain - 1000) / 1000}}({{time / 1000}}秒结束)</view>				
				</view>
				
			</template>
			
			
		</countdown-timer>
		<view class="reset-btn" @click="reset(time)">重置</view>
		<view class="reset-btn" @click="reset(1*60*60*1000)">重置为1小时</view>
		<view class="reset-btn" @click="reset(1*60*1000)">重置为1分钟</view>
		<view class="reset-btn" @click="reset(3000)">重置为3秒</view>
		
	</view>
</template>

<script module="test" lang="wxs">
	 module.exports = {
		msg: 'Hello'
	}
</script>
<script>
	export default {
		data() {
			return {
				time: new Date('2020/04/24 01:00:00').getTime() - new Date('2020/04/24 00:20:00').getTime()
			}
		},
		methods: {
			onFinish() {
				uni.showToast({
					icon: 'none',
					title: '倒计时结束'
				})
			},
			reset(time) {
				this.time = time
				this.$refs.countdown.restart()
			},
			fillWithZero(num, n) {
				var len = num.toString().length;
				while (len < n) {
					num = "0" + num;
					len++;
				}
				return num;
			}
		}
	}
</script>

<style>
	.container {
		padding: 20upx;
	}
	.case {
		display: flex;
		margin: 20upx;
	}
	.case > .title {
		margin-right: 10upx;
	}
	.custom {
		display: flex;
	}
	.custom :nth-child(odd) {
		background-color: red;
		padding: 2upx 4upx;
		color: white;
		border-radius: 5upx;
		text-align: center;
	}
	.custom :nth-child(even) {
		padding: 0 5upx;
	}
	.reset-btn {
		margin: 20upx 10upx;
		padding: 20upx;
		text-align: center;
		background-color: red;
		border-radius: 10upx;
		color: white;
	}
</style>
