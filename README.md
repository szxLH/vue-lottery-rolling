## 简介
> vue抽奖（老虎机）组件

使用方式：
npm install vue-lottery-rolling

需要用到该组件时可以这样引入

```javascript
import VueLotteryRolling from 'vue-lottery-rolling';

export default {
    name: 'app',
    components:{
        "vue-lottery-rolling": VueLotteryRolling
    }
}
```

使用案例
```javascript
<template>
    <div>
        <Lottery 
            :draw-text="drawText"    // 按钮显示文案
            :datasource="[goods, goods, goods]"  // 存储物品的二维数组
            :can-draw="canDraw"     // 能否抽奖
            :async-get-draw-result="asyncGetDrawResult"  // 抽奖的处理
            repeat="3" // 物品重复次数，默认为3
        />
    </div>
</template>

<script>

import VueLotteryRolling from 'vue-lottery-rolling';

export default {
    name: 'lottery',
    components: {
        VueLotteryRolling
    },
    data(){
        return {
            drawText: 'play',
            canDraw: true
        }
    },
    computed: {
        goods() {
            return [
                {src: require('./assets/AR.png')},
                {src: require('./assets/AU.png')},
                {src: require('./assets/BE.png')}
            ]
        }
    },
    methods: {
        asyncGetDrawResult () {
            // 抽奖动画结束后的回调
            let callback = (data) => {
                alert(`恭喜你抽中了${data.join('-')}`)
            }
            return new Promise((resolve, reject) => {
                // 这里进行异步操作
                let data = [1,2,3]
                resolve({
                    callback: callback.bind(this, data),
                    data: data
                })
            })
        }
    }
}

</script>

```

