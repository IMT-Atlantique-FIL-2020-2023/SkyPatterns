<template>
  <div class="split-container">
    <splitpanes class="default-theme" @resize="Resizing">
      <pane :size="side">
        <slot name="left"></slot>
      </pane>
      <pane>
        <slot name="right"></slot>
      </pane>
    </splitpanes>
  </div>
</template>
<script>
import { Splitpanes, Pane } from 'splitpanes'
import 'splitpanes/dist/splitpanes.css'
export default {
  name: 'SplitPane',
  components: { Splitpanes, Pane },
  props: {
    side: { type: Number, default: 50 },
    onResize: { type: Function, default: () => {} },
  },
  methods: {
    Resizing(event) {
      this.paneSize = event[0].size
      this.onResize()
    },
  },
}
</script>
<style lang="scss">
.split-container {
  padding: 0px;
  margin: 0px;
  height: 100%;
}
</style>
