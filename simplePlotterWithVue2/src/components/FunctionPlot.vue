<script setup lang="ts">
import { computed } from 'vue'

interface Props {
  fn: (x: number) => number
  xSamples: number
  xMin: number
  xMax: number
  yMin: number
  yMax: number
}

let props = defineProps<Props>()

let sampleStyles = computed(() => {
  let styleList: { height: string }[] = []

  for (let i = 0; i < props.xSamples; ++i) {
    let x = (i / props.xSamples) * (props.xMax - props.xMin) + props.xMin
    let y = Math.max(Math.min((props.fn(x) - props.yMin) / props.yMax, 1), 0)

    styleList.push({
      height: y * 100 + '%'
    })
  }

  return styleList
})
</script>

<template>
  <div class="functionPlot">
    <div v-for="(n, i) in xSamples" :key="n" class="plotSample" :style="sampleStyles[i]"></div>
  </div>
</template>

<style scoped lang="scss">
.functionPlot
{
  background-color: $bg-1;
  display: flex;
  flex-direction: row;
  align-items: flex-end;
  justify-content: flex-start;
}

.plotSample {
  background-color: $fg-1;
  width: 100%;
}
</style>
