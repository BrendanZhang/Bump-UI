<template>
  <div class="BUI-Switch" @click="toggle">
    <SwitchNormal
      :class="classes('', '', 'normal')"
      v-if="!retro"
      :flat="flat"
      :value="value"
      v-model:value="value"
    />
    <SwitchRetro
      :class="classes('', '', 'Retro')"
      v-if="retro"
      :value="value"
      v-model:value="value"
    />
  </div>
</template>

<script lang="ts">
import SwitchNormal from "./Switch.normal.vue";
import SwitchRetro from "./Switch.retro.vue";
import { classMaker } from "../common/classMaker";
export default {
  name: "BUI-Switch",
  components: { SwitchNormal, SwitchRetro },
  props: {
    value: Boolean,
    flat: {
      type: Boolean,
      default: false,
    },
    retro: {
      type: Boolean,
      default: false,
    },
  },
  setup(props, context) {
    const toggle = () => {
      context.emit("update:value", !props.value);
    };
    const classes = classMaker("BUI-Switch");
    return { toggle, classes };
  },
};
</script>

