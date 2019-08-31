<template>
  <div class="wrapper" ref="wrapper">
    <slot></slot>
  </div>
</template>
<script>
import BScroll from "better-scroll";
export default {
  name: "Scroll",
  props: {
    handleToScroll: {
      type: Function,
      default: function() {}
    },
    handleToTouchEnd: {
      type: Function,
      default: function() {}
    }
  },
  mounted() {
    var scroll = new BScroll(this.$refs.wrapper, {
      tap: true,
      probeType: 1
    });
    scroll.on("scroll", pos => {
      this.handleToScroll(pos);
    });
    scroll.on("scroll", pos => {
      this.handleToTouchEnd(pos);
    });
  }
};
</script>
<style scoped>
.wrapper {
  height: 100%;
}
</style>
    
