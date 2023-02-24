<template>
    <div>
        <span class="box">Box</span>
        <div class="options">
            <div class="effect" ref="effect"></div>
            <div class="item">
                <div class="itelli">
                    <span>height</span>
                    <Slider class="Slider" v-model="heightValue" show-input :max="max" :min="min" @on-input="heightFun"></Slider>
                </div>
                <div class="itelli">
                    <span>width</span>
                    <Slider class="Slider" v-model="widthValue" show-input :max="max" :min="min" @on-input="widthFun"></Slider>
                </div>
                <div class="itelli">
                    <span>radio</span>
                    <Slider
                        class="Slider"
                        v-model="borderRadiu"
                        :max="borderRadiuMax"
                        :min="borderRadiuMin"
                        show-input
                        @on-input="radiuFun"
                    ></Slider>
                </div>
                <div class="itelli">
                    <span>top left</span>
                    <Slider
                        class="borderSeparation"
                        v-model="topLeftValue"
                        :max="borderRadiuMax"
                        :min="borderRadiuMin"
                        @on-input="topLeftFun"
                    ></Slider>
                    <span>top right</span>
                    <Slider
                        class="borderSeparation"
                        v-model="topRightValue"
                        :max="borderRadiuMax"
                        :min="borderRadiuMin"
                        @on-input="topRightFun"
                    ></Slider>
                </div>
                <div class="itelli">
                    <span>bottom left</span>
                    <Slider
                        class="borderSeparation"
                        v-model="bottomLeftValue"
                        :max="borderRadiuMax"
                        :min="borderRadiuMin"
                        @on-input="bottomLeftFun"
                    ></Slider>
                    <span>bottom right</span>
                    <Slider
                        class="borderSeparation"
                        v-model="bottomRightValue"
                        :max="borderRadiuMax"
                        :min="borderRadiuMin"
                        @on-input="bottomRightFun"
                    ></Slider>
                </div>
                <div class="itelli last">
                    <span>border</span>
                    <Slider style="width: 300px" v-model="borderValue" @on-input="borderFun"></Slider>
                    <Select v-model="model" @on-change="borderFun" style="width: 250px">
                        <Option v-for="item in borderList" :value="item.value" :key="item.value">{{ item.label }}</Option>
                    </Select>
                    <ColorPicker class="color" v-model="borderColor" alpha @on-change="borderFun" />
                </div>
                <div class="itelli">
                    <div>
                        <span style="display: inline-block">backgroundColor</span>&nbsp;&nbsp;&nbsp;
                        <ColorPicker v-model="bgColor" alpha @on-change="bgColorFun" />
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
        this.$refs.effect.style.border = "8px dotted rgba(0, 0, 0, 0.5)";
    },
    data() {
        return {
            // 通用最大最校
            max: 400,
            min: 100,
            // 方块大小
            heightValue: 400,
            widthValue: 400,
            // 圆角大小
            borderRadiu: 0,
            // 圆角最大最小（根据方块大小变化）
            borderRadiuMax: 1,
            borderRadiuMin: 0,
            // 四个角的圆角大小
            topLeftValue: 0,
            topRightValue: 0,
            bottomLeftValue: 0,
            bottomRightValue: 0,
            // 边框样式
            borderList: [
                {
                    value: "none",
                    label: "无边框",
                },
                {
                    value: "dotted",
                    label: "点状(多数浏览器中呈现为实线)",
                },
                {
                    value: "dashed",
                    label: "虚线(大多数浏览器中呈现为实线)",
                },
                {
                    value: "solid",
                    label: "实线",
                },
                {
                    value: "double",
                    label: "双实线",
                },
                {
                    value: "groove",
                    label: " 3D凹槽",
                },
                {
                    value: "ridge",
                    label: "3D垄状",
                },
                {
                    value: "inset",
                    label: "3D inset",
                },
                {
                    value: "outset",
                    label: "3D outset",
                },
            ],
            model: "dotted",

            borderValue: 8,
            borderColor: "rgba(0, 0,0, 0.5)",
            bgColor: "rgba(166, 166, 166, 1.0)",
        };
    },
    methods: {
        heightFun() {
            this.$refs.effect.style.height = this.heightValue + "px";
        },

        widthFun() {
            this.$refs.effect.style.width = this.widthValue + "px";
        },

        radiuFun() {
            let heights = this.heightValue / 2;
            let widths = this.widthValue / 2;
            if (heights < widths || heights == widths) {
                this.borderRadiuMax = heights;
            } else if (heights > widths) {
                this.borderRadiuMax = widths;
            }
            (this.topLeftValue = 0),
                (this.topRightValue = 0),
                (this.bottomLeftValue = 0),
                (this.bottomRightValue = 0),
                (this.$refs.effect.style.borderRadius = this.borderRadiu + "px");
        },

        topLeftFun() {
            let heights = this.heightValue / 2;
            let widths = this.widthValue / 2;
            if (heights < widths || heights == widths) {
                this.borderRadiuMax = heights;
            } else if (heights > widths) {
                this.borderRadiuMax = widths;
            }
            this.$refs.effect.style.borderTopLeftRadius = this.topLeftValue + "px";
        },

        topRightFun() {
            let heights = this.heightValue / 2;
            let widths = this.widthValue / 2;
            if (heights < widths || heights == widths) {
                this.borderRadiuMax = heights;
            } else if (heights > widths) {
                this.borderRadiuMax = widths;
            }
            this.$refs.effect.style.borderTopRightRadius = this.topRightValue + "px";
        },

        bottomLeftFun() {
            let heights = this.heightValue / 2;
            let widths = this.widthValue / 2;
            if (heights < widths || heights == widths) {
                this.borderRadiuMax = heights;
            } else if (heights > widths) {
                this.borderRadiuMax = widths;
            }
            this.$refs.effect.style.borderBottomLeftRadius = this.bottomLeftValue + "px";
        },

        bottomRightFun() {
            let heights = this.heightValue / 2;
            let widths = this.widthValue / 2;
            if (heights < widths || heights == widths) {
                this.borderRadiuMax = heights;
            } else if (heights > widths) {
                this.borderRadiuMax = widths;
            }
            this.$refs.effect.style.borderBottomRightRadius = this.bottomRightValue + "px";
        },
        borderFun() {
            this.$refs.effect.style.border = `${this.borderValue}px ${this.model} ${this.borderColor}`;
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

.options .item .itelli .borderSeparation {
    width: 200px;
}

.options .item .last .Slider {
    width: 266px;
}
</style>
