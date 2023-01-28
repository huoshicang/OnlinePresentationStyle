<template>
  <div>
    <span class="box">Flex</span>
    <div class="options">
      <div class="effect">
        <div>1</div>
        <div>2</div>
        <div>3</div>
        <div>4</div>
        <div>5</div>
        <div>6</div>
        <div>7</div>
        <div>8</div>
        <div>9</div>
        <div>10</div>
        <div>11</div>
        <div>12</div>
      </div>
      <div class="item">
        <div class="itelli">
          <span>direction</span>
          <div>
            <button
              v-for="(direction, index) in directions"
              :key="index"
              :class="[direction_active == index ? 'active' : '']"
              @click="direction_cli(direction, index)"
            >
              {{ direction }}
            </button>
          </div>
        </div>
        <div class="itelli">
          <span>wrap</span>
          <div>
            <button
              v-for="(wrap, wrap_index) in wraps"
              :key="wrap_index"
              :class="[wrap_active == wrap_index ? 'active' : '']"
              @click="wrap_cli(wrap, wrap_index)"
            >
              {{ wrap }}
            </button>
          </div>
        </div>
        <div class="itelli">
          <span>justify-content</span>
          <div>
            <button
              v-for="(justify, justify_index) in justifys"
              :key="justify_index"
              :class="[justify_active == justify_index ? 'active' : '']"
              @click="justify_cli(justify, justify_index)"
            >
              {{ justify }}
            </button>
          </div>
        </div>
        <div class="itelli">
          <span>align-items</span>
          <div>
            <button
              v-for="(align, align_index) in aligns"
              :key="align_index"
              :class="[align_active == align_index ? 'active' : '']"
              @click="align_cli(align, align_index)"
            >
              {{ align }}
            </button>
          </div>
        </div>
        <div class="itelli">
          <span>align-content</span>
          <div>
            <button
              v-for="(align_content, align_content_index) in align_contents"
              :key="align_content_index"
              :class="[
                align_content_active == align_content_index ? 'active' : '',
              ]"
              @click="align_content_cli(align_content, align_content_index)"
            >
              {{ align_content }}
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { shallowReactive, shallowRef, onMounted } from "vue";
import "../assets/project.css";
var effect: any | null = null;

const directions = shallowReactive([
  "row",
  "row-reverse",
  "column",
  "column-reverse",
]);
const direction_active = shallowRef(0);
const direction_cli = (direction: any, direction_index: number) => {
  direction_active.value = direction_index;
  effect.style.flexDirection = direction;
};

const wraps = shallowReactive(["nowrap", "wrap", "wrap-reverse"]);
const wrap_active = shallowRef(0);
const wrap_cli = (wrap: any, wrap_index: number) => {
  effect.style.flexWrap = wrap;
  wrap_active.value = wrap_index;
};

const justifys = shallowReactive([
  "flex-start",
  "flex-end",
  "center",
  "space-between",
  "space-around",
]);
const justify_active = shallowRef(0);
const justify_cli = (justify: any, justify_index: number) => {
  effect.style.justifyContent = justify;
  justify_active.value = justify_index;
};

const aligns = shallowReactive([
  "flex-start",
  "flex-end",
  "center",
  "baseline",
  "stretch",
]);
const align_active = shallowRef(0);
const align_cli = (align: any, align_index: number) => {
  effect.style.alignItems = align;
  align_active.value = align_index;
};

const align_contents = shallowReactive([
  "flex-start",
  "flex-end",
  "center",
  "space-between",
  "space-around",
  "stretch",
]);
const align_content_active = shallowRef(0);
const align_content_cli = (align_content: any, align_content_index: number) => {
  effect.style.alignItems = align_content;
  align_content_active.value = align_content_index;
};

onMounted(() => {
  effect = document.querySelector(".effect");
});
</script>

<style scoped lange="less">
@media (max-width: 1000px) {
  .options {
    flex-direction: column;
    align-items: center;
  }
  .effect {
    flex: none;
    width: 300px;
  }
  .item {
    width: 300px;
    flex-wrap: wrap;
  }
}
.options {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
}
.effect {
  width: 400px;
  height: 400px;
  box-shadow: 0 0 10px #000000;
  display: inline-flex;
  transition: all 0.5s ease;
}
.effect div {
  height: 30px;
  width: 30px;
  background-color: aquamarine;
  margin: 5px;
  text-align: center;
  line-height: 30px;
}
.item {
  /* flex: 8; */
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  height: 400px;
  width: 1050px;
}
.item .itelli {
  height: 400px;
  width: 150px;
  box-shadow: 0 0 10px #ccc;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.item .itelli span {
  margin: 0;
  margin-top: 5px;
  font-size: 15px;
}
.item .itelli button {
  border: none;
  display: block;
  text-align: center;
  width: 125px;
  height: 50px;
  margin: 10px 0px;
  border-radius: 5px;
  transition: all 0.2s ease-in-out;
  font-weight: bold;
}
.item .itelli button:hover {
  border: 2px #ccc solid;
}

.active {
  color: rgb(79, 208, 131);
  font-size: 16px;
  background-color: rgba(204, 204, 204, 0.738);
}
.row {
  flex-direction: row;
}
.row-reverse {
  flex-direction: row-reverse;
}
.column {
  flex-direction: column;
}
.column-reverse {
  flex-direction: column-reverse;
}
.nowrap {
  flex-wrap: nowrap;
}
.wrap {
  flex-wrap: wrap;
}
.wrap-reverse {
  flex-wrap: wrap-reverse;
}
</style>
