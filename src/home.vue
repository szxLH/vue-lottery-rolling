<template>
    <div>
        <Lottery 
            :draw-text="drawText"
            :datasource="[goods, goods, goods]"
            :can-draw="canDraw"
            :async-get-draw-result="asyncGetDrawResult"
        />
    </div>
</template>

<script>

import Lottery from './lottery'

export default {
    name: 'lottery',
    components: {
        Lottery
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
            let callback = (data) => {
                alert(`恭喜你抽中了${data.join('-')}`)
            }
            return new Promise((resolve, reject) => {
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
