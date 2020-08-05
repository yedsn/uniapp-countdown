### 倒计时组件（自由定制版）

#### 效果展示
![效果展示](https://s1.ax1x.com/2020/08/05/asn43j.gif)

简单自由的时间倒计时组件，只封装倒计时逻辑，需要显示什么和显示的样式都由你控制。

****
#### 组件支持平台说明 ###
` H5亲测可用，其他平台没有详细测试过，如果其他平台出现什么问题留言回馈，我会抽时间修复的`

#### 使用示例

```html
<countdown-timer :time="time">
    <template v-slot="{day, hour, minute, second}">
        <view>{{day}}天{{hour}}时{{minute}}分{{second}}秒</view>		
    </template>
</countdown-timer>
```

#### 配置

- time [Number] 倒计时的毫秒数
- autoStart [Boolean] 是否自动启动倒计时

#### slot数据
- day 天
- hour 小时
- minute 分钟
- second 秒
- remain 剩余毫秒数

#### 事件

  - finish 倒计时结束事件

#### 组件可调用方法

  - start 开始倒计时
  - pause 暂停倒计时
  - reset 重置倒计时

*****

uniapp插件市场地址：https://ext.dcloud.net.cn/plugin?id=1687

github地址：https://github.com/yedsn/uniapp-countdown

`如果对你有帮助，请市场五星，github点个star，你的反馈是我继续开源的动力`