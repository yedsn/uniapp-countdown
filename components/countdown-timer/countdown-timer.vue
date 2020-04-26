<template>
	<view><slot :time="time" :remain="timeData.remain" :day="timeData.day" :hour="timeData.hour" :minute="timeData.minute" :second="timeData.second" /></view>
</template>

<script>
export default {
	props: {
		// 倒计时时长（单位：毫秒）
		time: {
			type: Number,
			default: 0
		}
	},
	data() {
		return {
			timer: null,
			timeData: {
				remain: 0,
				day: 0,
				hour: 0,
				minute: 0,
				second: 0
			}
		};
	},
	watch: {
		time() {
			this.timeData.remain = this.time;
			this.restart();
		}
	},
	methods: {
		startTimer() {
			this.updateTime();
			this.timer = setInterval(() => {
				this.updateTime();
			}, 1000);
		},
		updateTime() {
			let t = this.timeData.remain;
			this.timeData.day = Math.floor(t / 1000 / 60 / 60 / 24);
			this.timeData.hour = Math.floor((t / 1000 / 60 / 60) % 24);
			this.timeData.minute = Math.floor((t / 1000 / 60) % 60);
			this.timeData.second = Math.floor((t / 1000) % 60);
			this.timeData.remain -= 1000;
			if (this.timeData.remain < 0) {
				clearInterval(this.timer);
				this.$emit('finish');
			}
		},
		restart() {
			if (this.timer != null) {
				clearInterval(this.timer);
			}
			this.timeData.remain = this.time;
			this.startTimer();
		}
	},
	mounted() {
		this.timeData.remain = this.time;
		this.startTimer();
	},
	beforeDestroy() {
		clearInterval(this.timer);
	}
};
</script>
