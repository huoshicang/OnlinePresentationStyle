<template>
    <div>
        <span class="box">Font shadow</span>
        <div class="options">
            <h1 ref="h1">离无歌</h1>
            <div class="item">
                <div class="itelli">
                    <span>大小</span>
                    <Slider style="width: 700px" v-model="value1" :max="max" @on-input="sizeFun" :show-stops="showStops"></Slider>
                </div>
                <div class="itelli">
                    <span>X</span>
                    <Slider class="Slider" v-model="xValue" :max="XandYmax" :min="min" @on-input="Fun"></Slider>
                </div>
                <div class="itelli">
                    <span>Y</span>
                    <Slider class="Slider" v-model="yValue" :max="XandYmax" :min="min" @on-input="Fun"></Slider>
                </div>
                <div class="itelli">
                    <span>模糊</span>
                    <Slider class="Slider" show-stops v-model="spreadValue" :max="spreadMax" :min="0" @on-input="Fun"></Slider>
                </div>
                <div class="itelli">
                    <div>颜色：<ColorPicker v-model="color" alpha @on-change="Fun" /></div>
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
        this.$refs.h1.style.textShadow = `${this.xValue}px ${this.yValue}px ${this.spreadValue}px ${this.color}`;
    },
    data() {
        return {
            value1: 28,
            XandYmax: 50,
            min: -50,
            xValue: 5,
            yValue: 5,
            spreadValue: 2,
            spreadMax: 10,
            color: "rgba(166, 166, 166, 1.0)",
        };
    },
    methods: {
        Fun() {
            this.$refs.h1.style.textShadow = `${this.xValue}px ${this.yValue}px ${this.spreadValue}px ${this.color}`;
        },
        sizeFun() {
            this.$refs.h1.style.fontSize = this.value1 + "px";
        },
    },
};
</script>

<style scoped lange="less">
@media (max-width: 1000px) {
    .options {
        flex-direction: column;
        align-items: center;
        transform: translateY(164px);
    }
    .effect {
        flex: none;
        width: 300px;
    }
    .item {
        margin-top: -85px;
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
