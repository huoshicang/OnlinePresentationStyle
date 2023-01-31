<template>
    <div>
        <span class="box">Box</span>
        <div class="options">
            <div class="effect" ref="effect"></div>
            <div class="item">
                <div class="itelli">
                    <span>height</span>
                    <Slider
                        class="Slider"
                        v-model="heightValue"
                        show-input
                        :max="max"
                        :min="min"
                        @on-input="heightFun(heightValue)"
                    ></Slider>
                </div>
                <div class="itelli">
                    <span>width</span>
                    <Slider
                        class="Slider"
                        v-model="widthValue"
                        show-input
                        :max="max"
                        :min="min"
                        @on-input="widthFun(widthValue)"
                    ></Slider>
                </div>
                <div class="itelli">
                    <span>radio</span>
                    <Slider
                        class="Slider"
                        v-model="borderRadiu"
                        :max="borderRadiuMax"
                        :min="borderRadiuMin"
                        show-input
                        @on-input="radiuFun(borderRadiu)"
                    ></Slider>
                </div>
                <div class="itelli">
                    <span>top left</span>
                    <Slider
                        class="borderSeparation"
                        v-model="topLeftValue"
                        :max="borderRadiuMax"
                        :min="borderRadiuMin"
                        @on-input="topLeftFun(topLeftValue)"
                    ></Slider>
                    <span>top right</span>
                    <Slider
                        class="borderSeparation"
                        v-model="topRightValue"
                        :max="borderRadiuMax"
                        :min="borderRadiuMin"
                        @on-input="topRightFun(topRightValue)"
                    ></Slider>
                </div>
                <div class="itelli">
                    <span>bottom left</span>
                    <Slider
                        class="borderSeparation"
                        v-model="bottomLeftValue"
                        :max="borderRadiuMax"
                        :min="borderRadiuMin"
                        @on-input="bottomLeftFun(bottomLeftValue)"
                    ></Slider>
                    <span>bottom right</span>
                    <Slider
                        class="borderSeparation"
                        v-model="bottomRightValue"
                        :max="borderRadiuMax"
                        :min="borderRadiuMin"
                        @on-input="bottomRightFun(bottomRightValue)"
                    ></Slider>
                </div>
                <div class="itelli last">
                    <span>border</span>
                    <Slider style="width: 300px" v-model="borderValue" @on-input="borderFun(borderValue)"></Slider>
                    <Select v-model="model" style="width: 250px">
                        <Option v-for="item in borderList" :value="item.value" :key="item.value">{{ item.label }}</Option>
                    </Select>
                    <ColorPicker class="color" v-model="borderColor" alpha @on-change="borderColorFun(borderColor)" />
                </div>
                <div class="itelli">
                    <span>backgroundColor</span>
                    <ColorPicker v-model="bgColor" alpha @on-change="bgColorFun(bgColor)" />
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
            model: "none",

            borderValue: 10,
            borderStyle: null,
            borderColor: "rgba(0, 0,0, 0.5)",
            bgColor: "rgba(166, 166, 166, 1.0)",
        };
    },
    methods: {
        heightFun(heightValue) {
            this.$refs.effect.style.height = heightValue + "px";
        },

        widthFun(widthValue) {
            this.$refs.effect.style.width = widthValue + "px";
        },

        radiuFun(borderRadiu) {
            let heights = this.heightValue / 2;
            let widths = this.widthValue / 2;
            if (heights < widths || heights == widths) {
                this.borderRadiuMax = heights;
            } else if (heights > widths) {
                this.borderRadiuMax = widths;
            }
            this.$refs.effect.style.borderRadius = borderRadiu + "px";
        },

        topLeftFun(topLeftValue) {
            let heights = this.heightValue / 2;
            let widths = this.widthValue / 2;
            if (heights < widths || heights == widths) {
                this.borderRadiuMax = heights;
            } else if (heights > widths) {
                this.borderRadiuMax = widths;
            }
            this.$refs.effect.style.borderTopLeftRadius = topLeftValue + "px";
        },

        topRightFun(topRightValue) {
            let heights = this.heightValue / 2;
            let widths = this.widthValue / 2;
            if (heights < widths || heights == widths) {
                this.borderRadiuMax = heights;
            } else if (heights > widths) {
                this.borderRadiuMax = widths;
            }
            this.$refs.effect.style.borderTopRightRadius = topRightValue + "px";
        },

        bottomLeftFun(bottomLeftValue) {
            let heights = this.heightValue / 2;
            let widths = this.widthValue / 2;
            if (heights < widths || heights == widths) {
                this.borderRadiuMax = heights;
            } else if (heights > widths) {
                this.borderRadiuMax = widths;
            }
            this.$refs.effect.style.borderBottomLeftRadius = bottomLeftValue + "px";
        },

        bottomRightFun(bottomRightValue) {
            let heights = this.heightValue / 2;
            let widths = this.widthValue / 2;
            if (heights < widths || heights == widths) {
                this.borderRadiuMax = heights;
            } else if (heights > widths) {
                this.borderRadiuMax = widths;
            }
            this.$refs.effect.style.borderBottomRightRadius = bottomRightValue + "px";
        },
        //未完成
        borderFun(borderValue) {
            this.$refs.effect.style.border = borderValue + "px";
        },
        //边框样式未完成
        //未完成
        borderColorFun(borColor) {
            this.$refs.effect.style.borderColor = borColor;
        },

        bgColorFun(bgColor) {
            this.$refs.effect.style.backgroundColor = bgColor;
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
        width: 300px;
        flex-wrap: wrap;
        transform: translateX(-257px);
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
    box-shadow: 0 0 10px #000000;
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
