<template>
  <div class="d2-container-full" :style="cardStyle">
    <div v-if="$slots.header" class="d2-container-full__header" ref="header">
      <slot name="header"/>
    </div>
    <div class="d2-container-full__body" :style="bodyStyle">
      <slot/>
    </div>
    <div v-if="$slots.footer" class="d2-container-full__footer" ref="footer">
      <slot name="footer"/>
    </div>
  </div>
</template>

<script>
export default {
  name: 'd2-container-full',
  props: {
    // 定位 上 右 下 左
    top: {
      type: Number,
      required: false,
      default: 0
    },
    right: {
      type: Number,
      required: false,
      default: 0
    },
    bottom: {
      type: Number,
      required: false,
      default: 0
    },
    left: {
      type: Number,
      required: false,
      default: 0
    }
  },
  data () {
    return {
      headerHeight: 0,
      footerHeight: 0
    }
  },
  mounted () {
    this.headerHeight = this.$slots.header ? this.$refs.header.offsetHeight : 0
    this.footerHeight = this.$slots.footer ? this.$refs.footer.offsetHeight : 0
  },
  computed: {
    cardStyle () {
      return {
        top: `${this.top}px`,
        right: `${this.right}px`,
        bottom: `${this.bottom}px`,
        left: `${this.left}px`
      }
    },
    bodyStyle () {
      return {
        top: `${this.headerHeight}px`,
        bottom: `${this.footerHeight}px`
      }
    }
  }
}
</script>
