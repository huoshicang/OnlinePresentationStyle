<template>
    <div>
        <span class="box">Opacity</span>
        <div class="options">
            <div class="effect" ref="effect"></div>
            <div class="item">
                <div class="itelli">
                    <span>透明度</span>
                    <Slider style="width: 700px" v-model="opacity" :max="100" :min="0" @on-input="opacityFun"></Slider>
                </div>
                <div class="itelli">
                    <div>
                        <span style="display: inline-block">backgroundColor</span>&nbsp;&nbsp;&nbsp;
                        <ColorPicker v-model="bgColor" @on-change="bgColorFun(bgColor)" />
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
        this.$refs.effect.style.backgroundColor = this.bgColor;
    },
    data() {
        return {
            opacity: 100,
            bgColor: "rgb(0, 0, 0)",
        };
    },
    methods: {
        opacityFun() {
            this.$refs.effect.style.opacity = `${this.opacity}%`;
        },
        bgColorFun() {
            this.$refs.effect.style.backgroundColor = this.bgColor;
        },
    },
};
</script>

<style scoped lange="less">
.options {
    height: 400px;
    display: flex;
    align-items: center;
    justify-content: space-evenly;
}
.effect {
    width: 400px;
    height: 400px;
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
