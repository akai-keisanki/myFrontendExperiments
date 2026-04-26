<script setup lang="ts">
import { ref, reactive, computed } from 'vue'

import FunctionPlot from '../components/FunctionPlot.vue'

let fStr = ref('(Math.sin(x/7)*7)**2')

let pltSts = reactive({
  minX: 0,
  maxX: 100,
  minY: 0,
  maxY: 50,
  xSamples: 1000
})

let f = computed(() => (x) => eval(fStr.value))
</script>

<template>
  <main>
    <div id="controls">
      <div class="control">
        <label for="minX">minX</label>
        <input name="minX" type="number" v-model="pltSts.minX" />
      </div>
      <div class="control">
        <label for="maxX">maxX</label>
        <input name="maxX" type="number" v-model="pltSts.maxX" />
      </div>
      <div class="control">
        <label for="minY">minY</label>
        <input name="minY" type="number" v-model="pltSts.minY" />
      </div>
      <div class="control">
        <label for="maxY">maxY</label>
        <input name="maxY" type="number" v-model="pltSts.maxY" />
      </div>
      <div class="control">
        <label for="xSamples">xSamples</label>
        <input name="xSamples" type="number" v-model="pltSts.xSamples" />
      </div>
      <div class="control">
        <label for="fStr">function</label>
        <input name="fStr" type="text" v-model="fStr" />
      </div>
    </div>
    <FunctionPlot
      id="plot"
      :fn="f"
      :xMin="pltSts.minX"
      :xMax="pltSts.maxX"
      :yMin="pltSts.minY"
      :yMax="pltSts.maxY"
      :xSamples="pltSts.xSamples"
    />
  </main>
</template>

<style scoped lang="scss">
main {
  min-height: 100vh;

  display: grid;
  grid-template-areas: 'controls' 'plot';
  grid-template-rows: 40vh auto;
}

#controls {
  grid-area: controls;
  display: flex;
  flex-direction: row;
  align-items: flex-end;
  justify-content: center;
}

#plot {
  grid-area: plot;
  display: flex;
}

.control {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
