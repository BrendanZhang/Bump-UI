<demo>基本用法</demo>
<template>
  <section>
    <Tabs v-model:selected="tabsValue">
      <Tab title="导航1">
        <div>内容1</div>
        <p>内容1</p>
        <div>内容1</div>
      </Tab>
      <Tab title="导航3">
        <div>内容3</div>
        <div>内容3</div>
        <div>内容3</div>
        <div>内容3</div>
      </Tab>
    </Tabs>
  </section>
</template>

<script>
import Tabs from '../../lib/Tabs/Tabs.vue'
import Tab from '../../lib/Tabs/Tab.vue'
import { ref } from 'vue';
export default {
  name: "TabsDemo",
  components:{
    Tabs,
    Tab
  },
  setup(){
    const tabsValue = ref('导航1')
    return {tabsValue}
  }
};
</script>