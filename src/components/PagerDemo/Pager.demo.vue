<template>
  <div class="pager">
    <h1>Pager 组件</h1>
    <Demo :component="PagerDemo1" defaultVisible>
      <p>Pager 基本用法 接受 totalPage 总页数和 currentPage 当前页</p>
    </Demo>
    <Demo :component="PagerDemo2" defaultVisible>
      <p>接受 hideIfOnePage 在只有一页的时候隐藏分页器，默认为 true</p>
    </Demo>
    <AttrTable title="Pager Attributes" :sourceData="pagerAttr" />
  </div>
</template>

<script lang="ts" scoped>
import AttrTable from '../AttrTable.vue';
import Demo from "../Demo.vue";
import PagerDemo1 from './Pager.demo1.vue'
import PagerDemo2 from './Pager.demo2.vue'
export default {
  name: "SwitchDemo",
  components: { Demo, AttrTable },
  setup() {

    const pagerAttr = [
      {
        id: 0,
        attr: 'totalPage',
        content: "确定总页数",
        type: 'number',
        option: '',
        default: '',
        required: 'true',
        description: ''
      },
      {
        id: 1,
        attr: 'currentPage',
        content: "当前页码",
        type: 'number',
        option: '',
        default: '',
        required: 'true',
        description: ''
      },
      {
        id: 2,
        attr: 'hideIfOnePage',
        content: "若只有一页的话隐藏 pager",
        type: 'boolean',
        option: '',
        default: 'true',
        required: 'false',
        description: ''
      },
    ]

    return {
      PagerDemo1,
      PagerDemo2,
      pagerAttr
    };
  },
}
</script>

<style lang="scss">
.pager {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  width: 100%;
  .switchSection {
    display: flex;
    justify-content: flex-start;
    align-items: flex-start;
    flex-wrap: wrap;
    width: 100%;
  }
}
</style>
