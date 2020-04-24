### 倒计时组件（自由定制版）

#### 效果展示
![效果展示](http://p2.so.qhmsg.com/t02ed82442262902b46.jpg)

简单自由的时间倒计时组件，只封装倒计时逻辑，需要显示什么和显示的样式都由你控制。

****

#### 使用示例

```html
<countdown-timer :time="time">
    <template v-slot="{day, hour, minute, second}">
        <view>{{day}}天{{hour}}时{{minute}}分{{second}}秒</view>		
    </template>
</countdown-timer>
```

#### 配置

- time 倒计时的毫秒数

#### slot数据
- day 天
- hour 小时
- minute 分钟
- second 秒
- remain 剩余毫秒数

#### 事件

  - finish 倒计时结束事件

#### 组件可调用方法

  - restart 重新开始倒计时

*****

uniapp插件市场地址：https://ext.dcloud.net.cn/plugin?id=1687

github地址：https://github.com/yedsn/uniapp-countdown

如果对你有帮助，请市场五星，github点个star，你的反馈是我继续开源的动力