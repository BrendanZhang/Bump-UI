<template>
  <div class="BUI-Col" :class="colClass" :style="colStyle">
    <slot></slot>
  </div>
</template>

<script lang="ts">
import { computed, inject, ref } from 'vue';
const validator = value => {
  let keys = Object.keys(value);
  let valid = true;
  keys.forEach(key => {
    if (!["span", "offset"].includes(key)) {
      valid = false;
    }
  });
  return valid;
};
export default {
  name: "BUI-Col",
  props: {
    span: {
      type: [Number, String]
    },
    offset: {
      type: [Number, String]
    },
    pad: {
      type: Object,
      validator
    },
    narrowPc: {
      type: Object,
      validator
    },
    pc: {
      type: Object,
      validator
    },
    widePc: {
      type: Object,
      validator
    }
  },
  setup(props, context) {
    const gutter = inject<string | number>('gutter')


    const selectClass = (spanAndOffSet, string = "") => {
      // ipad- or pc-
      if (!spanAndOffSet) {
        return [];
      }
      let array = [];
      if (spanAndOffSet.span) {
        array.push(`col-${string}${spanAndOffSet.span}`);
      }
      if (spanAndOffSet.offset) {
        array.push(`offset-${string}${spanAndOffSet.offset}`);
      }
      return array;
    }

    const colClass = computed(() => {
      let { span, offset, pad, narrowPc, pc, widePc } = props
      let selectClassFunc = selectClass
      return [
        ...selectClassFunc({ span, offset }),
        ...selectClassFunc(pad, "pad-"),
        ...selectClassFunc(narrowPc, "narrow-pc-"),
        ...selectClassFunc(pc, "pc-"),
        ...selectClassFunc(widePc, "wide-pc-")
      ];
    })

    const gutterToNumber = (gutter: string | number) => {
      if (typeof gutter === 'string') {
        return parseInt(gutter)
      } else {
        return gutter
      }
    }

    const colStyle = computed(() => {
      return {
        paddingLeft: gutterToNumber(gutter) / 2 + "px",
        paddingRight: gutterToNumber(gutter) / 2 + "px"
      };
    })

    return {
      gutter,
      colClass,
      colStyle
    };
  }
};
</script>

