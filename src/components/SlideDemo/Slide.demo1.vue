<demo>
默认 Slide 轮播
</demo>
<template>
  <div>
    <Slides v-model:selected="selected">
      <Slides-item name="1">
        <div class="box-1">1</div>
      </Slides-item>
      <Slides-item name="2">
        <div class="box-2">2</div>
      </Slides-item>
      <Slides-item name="3">
        <div class="box-3">3</div>
      </Slides-item>
    </Slides>
  </div>
</template>
<script lang="ts">
import Slides from "../../lib/Slides/Slides.vue";
import SlidesItem from "../../lib/Slides/Slides-item.vue";
import { ref } from "vue";
export default {
  name: "demo",
  components: { Slides, SlidesItem },
  setup() {
    const selected = ref("2");
    return {
      selected,
    };
  },
};
</script>
<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.wrapper {
  padding: 0;
  margin: 0;
}
.box {
  width: 100%;
  height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 30px;
  &-1 {
    @extend .box;
    background: white;
    color: black;
  }
  &-2 {
    @extend .box;
    background: grey;
    color: black;
  }
  &-3 {
    @extend .box;
    background: black;
    color: white;
  }
}
</style>
