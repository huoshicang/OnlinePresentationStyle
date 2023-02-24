<template>
    <div>
        <span class="box">Text</span>
        <div class="options">
            <h1 ref="h1">离无歌</h1>
            <div class="item">
                <div class="size">
                    大小<Slider style="width: 700px" v-model="value1" :max="max" @on-input="sizeFun" :show-stops="showStops">
                    </Slider>
                    单位<Select v-model="sizeModel" style="width: 65px" @on-change="selectFun">
                        <Option v-for="item in sizeList" :value="item.value" :key="item.value">{{ item.label }}</Option>
                    </Select>
                </div>
                <div class="itelli">
                    <div>下划线： <Switch class="switch" v-model="underlineValue" @on-change="decoration('underline')" /></div>
                    <div>
                        中划线： <Switch class="switch" v-model="lineThroughValue" @on-change="decoration('line-through')" />
                    </div>
                    <div>上划线： <Switch class="switch" v-model="overlineValue" @on-change="decoration('overline')" /></div>
                </div>
                <div class="itelli">
                    <div>
                        加粗：<Select v-model="weightModel" class="weight" @on-change="weighttFun">
                            <Option v-for="item in weightList" :value="item.value" :key="item.value">{{ item.label }}</Option>
                        </Select>
                    </div>
                    <div>倾斜：<Switch class="switch" v-model="obliqueValue" @on-change="obliqueFun" /></div>
                </div>
                <div class="itelli">
                    <div>字体颜色：<ColorPicker style="width: 250px" v-model="color" alpha @on-change="colorFun" /></div>
                </div>
            </div>
        </div>

        <div></div>
    </div>
</template>

<script setup lang="ts">
import {} from "vue";
</script>

<script lang="ts">
export default {
    data() {
        return {
            value1: 2,
            max: 10,
            showStops: true,
            sizeList: [
                {
                    value: "px",
                    label: "px",
                },
                {
                    value: "em",
                    label: "em",
                },
                {
                    value: "rem",
                    label: "rem",
                },
                {
                    value: "%",
                    label: "%",
                },
            ],
            sizeModel: "em",
            underlineValue: false,
            lineThroughValue: false,
            overlineValue: false,
            weightList: [
                {
                    value: "normal",
                    label: "normal",
                },
                {
                    value: "bold",
                    label: "bold",
                },
                {
                    value: "bolder",
                    label: "bolder",
                },
                {
                    value: "lighter",
                    label: "lighter",
                },
                {
                    value: "100",
                    label: "100",
                },
                {
                    value: "200",
                    label: "200",
                },
                {
                    value: "300",
                    label: "300",
                },
                {
                    value: "400",
                    label: "400",
                },
                {
                    value: "500",
                    label: "500",
                },
                {
                    value: "600",
                    label: "600",
                },
                {
                    value: "700",
                    label: "700",
                },
                {
                    value: "800",
                    label: "800",
                },
                {
                    value: "900",
                    label: "900",
                },
            ],
            weightModel: "normal",
            obliqueValue: false,
            color: "rgba(0, 0, 0, 1.0)",
        };
    },

    methods: {
        sizeFun() {
            this.$refs.h1.style.fontSize = this.value1 + this.sizeModel;
        },
        selectFun() {
            if (this.sizeModel == "px") {
                this.max = 300;
                this.value1 = 50;
                this.showStops = !this.showStops;
            } else {
                this.max = 10;
                this.value1 = 2;
                this.showStops = !this.showStops;
            }
            this.$refs.h1.style.fontSize = this.value1 + this.sizeModel;
        },
        decoration(val) {
            if (val == "overline") {
                this.lineThroughValue = false;
                this.underlineValue = false;
                if (this.overlineValue) {
                    this.$refs.h1.style.textDecoration = val;
                } else {
                    this.$refs.h1.style.textDecoration = "";
                }
            } else if (val == "line-through") {
                this.overlineValue = false;
                this.underlineValue = false;
                if (this.lineThroughValue) {
                    this.$refs.h1.style.textDecoration = val;
                } else {
                    this.$refs.h1.style.textDecoration = "";
                }
            } else if (val == "underline") {
                this.overlineValue = false;
                this.lineThroughValue = false;
                if (this.underlineValue) {
                    this.$refs.h1.style.textDecoration = val;
                } else {
                    this.$refs.h1.style.textDecoration = "";
                }
            }
        },
        weighttFun() {
            this.$refs.h1.style.fontWeight = this.weightModel;
        },
        obliqueFun() {
            if (this.obliqueValue) {
                this.$refs.h1.style.fontStyle = "oblique";
            } else {
                this.$refs.h1.style.fontStyle = "";
            }
        },
        colorFun() {
            this.$refs.h1.style.color = this.color;
        },
    },
};
</script>

<style scoped lange="less">
.options {
    display: flex;
    align-items: center;
    justify-content: space-evenly;
    flex-direction: column;
}
.options .item {
    display: flex;
    flex-direction: column;
}
.options .item .size {
    display: inline-flex;
    align-items: center;
}
.options .item .size * {
    margin: 10px;
}
.options .item .itelli {
    width: 835px;
    height: auto;
    display: inline-flex;
    justify-content: space-around;
    align-items: center;
    margin: 8px 0;
}

.options .item .itelli .weight {
    width: 200px;
}
</style>
