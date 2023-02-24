<template>
    <div class="main">
        <div class="top">
            <ul>
                <li
                    v-for="(project, index) in projects"
                    :key="index"
                    @click="cli(project, index)"
                    :class="[active == index ? 'active' : '']"
                >
                    <a :href="'#' + project.name">{{ project.name }}</a>
                </li>
            </ul>
        </div>
        <div class="buttom">
            <component :is="comId"></component>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref, reactive } from "vue";
import Flex from "./components/Flex.vue";
import Box from "./components/Box.vue";
import Text from "./components/Text.vue";
import Box_shadow from "./components/Box_shadow.vue";
import Font_shadow from "./components/Font_shadow.vue";
import Opacity from "./components/Opacity.vue";
type data = {
    name: string;
    flage: any;
};
const projects = reactive<data[]>([
    {
        name: "Flex",
        flage: Flex,
    },
    {
        name: "Box",
        flage: Box,
    },
    {
        name: "Text",
        flage: Text,
    },
    {
        name: "Box_shadow",
        flage: Box_shadow,
    },
    {
        name: "Font_shadow",
        flage: Font_shadow,
    },
    {
        name: "Opacity",
        flage: Opacity,
    },
]);

const comId = ref(),
    active = ref();
const cli = (item: any, index: number) => {
    comId.value = item.flage;
    active.value = index;
};
</script>

<style scoped lange="less">
.main {
    display: flex;
    width: 100%;
    overflow-x: hidden;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
.top {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 50px;
}
.buttom {
    height: 600px;
    width: 90%;
}
.top a {
    display: inline-block;
    width: 100%;
    height: 100%;
    color: rgb(79, 208, 131);
    font-weight: bold;
    text-align: center;
    line-height: 60px;
    transition: all 0.2s cubic-bezier(0.22, 0.02, 0.9, 0.75);
    border-radius: 5px;
}
.top ul {
    display: flex;
}
.top ul li {
    height: 60px;
    width: 200px;
    border: 2px solid #ccc;
    margin: 10px;
    border-radius: 8px;
    transition: all 0.2s ease-in-out;
    font-size: 17px;
}
.top ul li a:hover {
    color: #fff;
    background-color: #ccc;
}
.active a {
    font-size: 25px;
}
</style>
