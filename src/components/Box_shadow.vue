<template>
    <div>
        <span class="box">Box shadow</span>
        <div class="options">
            <div class="effect" ref="effect"></div>
            <div class="item">
                <div class="itelli">
                    <span>X</span>
                    <Slider class="Slider" v-model="xValue" :max="XandYmax" :min="min" @on-input="Fun"></Slider>
                </div>
                <div class="itelli">
                    <span>Y</span>
                    <Slider class="Slider" v-model="yValue" :max="XandYmax" :min="min" @on-input="Fun"></Slider>
                </div>
                <div class="itelli">
                    <span>半径</span>
                    <Slider class="Slider" v-model="radiusValue" :max="radiusMax" :min="min + 50" @on-input="Fun"></Slider>
                </div>
                <div class="itelli">
                    <span>扩散</span>
                    <Slider class="Slider" v-model="spreadValue" :max="spreadMax" :min="min + 50" @on-input="Fun"></Slider>
                </div>
                <div class="itelli">
                    <div>颜色：<ColorPicker v-model="color" alpha @on-change="Fun" /></div>
                    <div style="display: inline-flex">
                        外阴影&nbsp;&nbsp;&nbsp;&nbsp;<Switch
                            class="switch"
                            v-model="bump"
                            @on-change="Fun"
                        />&nbsp;&nbsp;&nbsp;&nbsp;内阴影
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import {} from "vue";
</script>

<script lang="ts">
export default {
    mounted() {
        this.$refs.effect.style.boxShadow = `5px 5px 10px 10px rgba(166, 166, 166, 1.0)`;
    }, // mounted在模板渲染成html后调用
    data() {
        return {
            XandYmax: 50,
            min: -50,
            xValue: 5,
            yValue: 5,
            radiusValue: 10,
            radiusMax: 200,
            spreadValue: 10,
            spreadMax: 100,
            color: "rgba(166, 166, 166, 1.0)",
            bump: false,
        };
    }, // data() 为变量赋值等
    methods: {
        Fun() {
            if (this.bump) {
                this.$refs.effect.style.boxShadow = `inset ${this.xValue}px ${this.yValue}px ${this.radiusValue}px ${this.spreadValue}px ${this.color}`;
            } else {
                this.$refs.effect.style.boxShadow = `${this.xValue}px ${this.yValue}px ${this.radiusValue}px ${this.spreadValue}px ${this.color}`;
            }
        },
    }, // methods 编写js函数
};
</script>

<style scoped lange="less">
@media (max-width: 1000px) {
    .options {
        flex-direction: column;
        align-items: center;
        margin-top: 127px;
    }
    .effect {
        flex: none;
        width: 300px;
    }
    .item {
        margin-top: -50px;
        width: 300px;
        flex-wrap: wrap;
        transform: translateX(-125px) scale(0.5);
    }
}
.options {
    height: 400px;
    display: flex;
    align-items: center;
    justify-content: space-evenly;
}
.effect {
    width: 400px;
    height: 400px;
    border: 1px black solid;
}
.ivu-switch-checked {
    border-color: #ccc;
    background-color: #ccc;
}
.options .item {
    display: flex;
    flex-direction: column;
}
.options .item .itelli {
    width: 835px;
    height: auto;
    display: inline-flex;
    justify-content: space-around;
    align-items: center;
    margin: 8px 0;
}
.options .item .itelli span {
    display: block;
    font-size: 2em;
    font-weight: bold;
}
.options .item .itelli .Slider {
    width: 700px;
}
</style>
