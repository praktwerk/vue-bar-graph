<template>
  <div id="app">
    <vue-bar-graph
      :points="dataPoints"
      :width="chartWidth"
      :height="chartHeight"
      :show-values="true"
    />
    <br>
    <br>
    <vue-bar-graph
      :show-y-axis="true"
      :points="dataPoints"
      :width="chartWidth"
      :height="chartHeight"
    />
    <br>
    <br>
    <vue-bar-graph
      :max-y-axis="50"
      :show-y-axis="true"
      :points="dataPoints"
      :width="chartWidth"
      :height="chartHeight"
    />
    <br>
    <br>
    <vue-bar-graph
      :max-y-axis="50"
      :show-y-axis="true"
      :show-x-axis="true"
      :points="dataPoints"
      :width="chartWidth"
      :height="chartHeight"
    />
    <br>
    <br>
    <vue-bar-graph
      :show-y-axis="true"
      :show-x-axis="true"
      :points="dataPoints"
      :width="chartWidth"
      :height="chartHeight"
      :use-custom-labels="true"
      :custom-labels="monthLabels"
      :show-trend-line="true"
      :trend-line-width="2"
      trend-line-color="lightblue"
    />
    <br>
    <br>
    <vue-bar-graph
      :show-y-axis="false"
      :show-x-axis="true"
      :points="dataPoints"
      :width="chartWidth"
      :height="chartHeight"
      :show-values="true"
      :use-custom-labels="true"
      :custom-labels="monthLabels"
      :animation-duration="2"
      bar-color="lightpink"
    />
    <br>
    <br>
    <vue-bar-graph
      :show-y-axis="false"
      :show-x-axis="true"
      :points="dataPointObjects"
      :width="chartWidth"
      :height="chartHeight"
      :show-values="true"
    />
    <br>
    <br>
    <vue-bar-graph
      :show-y-axis="false"
      :show-x-axis="true"
      :points="dataPointObjects"
      :width="chartWidth"
      :height="chartHeight"
      :show-values="true"
      :label-height="20"
      text-color="grey"
    >
      <template v-slot:label="opt">
        <text
          v-if="opt.bar.index === 1"
          :x="opt.bar.midPoint"
          :y="`${opt.bar.yLabel + 10}px`"
          text-anchor="middle"
          :style="opt.textStyle"
        >
          Here
        </text>
        <text
          v-else-if="opt.bar.index === 2"
          :x="opt.bar.midPoint"
          :y="`${opt.bar.yLabel + 10}px`"
          text-anchor="middle"
          :style="opt.textStyle"
        >
          are
        </text>
        <text
          v-else-if="opt.bar.index === 3"
          :x="opt.bar.midPoint"
          :y="`${opt.bar.yLabel + 10}px`"
          text-anchor="middle"
          :style="opt.textStyle"
        >
          custom
        </text>
        <text
          v-else-if="opt.bar.index === 4"
          :x="opt.bar.midPoint"
          :y="`${opt.bar.yLabel + 10}px`"
          text-anchor="middle"
          :style="opt.textStyle"
        >
          labels
        </text>
        <image
          v-else-if="opt.bar.index === 5"
          :x="`${opt.bar.midPoint - 10}px`"
          :y="`${opt.bar.yLabel}px`"
          height="20"
          width="20"
          href="https://raw.githubusercontent.com/vuejs/art/master/logo.png"
        />
        <text
          v-else-if="opt.bar.index === 6"
          :x="opt.bar.midPoint"
          :y="`${opt.bar.yLabel + 10}px`"
          text-anchor="middle"
          :style="opt.textStyle"
        >
          &#128526;
        </text>
        <text
          v-else
          :x="opt.bar.midPoint"
          :y="`${opt.bar.yLabel + 10}px`"
          text-anchor="middle"
          :style="opt.textStyle"
        >
          {{ opt.bar.label }}
        </text>
      </template>
      <template v-slot:title="props">
        <tspan v-if="props.bar.index === 5">
          Very custom title text
        </tspan>
        <tspan v-else>
          {{ props.bar.staticValue }}
        </tspan>
      </template>
    </vue-bar-graph>
  </div>
</template>

<script>
import VueBarGraph from './components/VueBarGraph.vue';

export default {
  name: 'App',
  components: {
    VueBarGraph,
  },
  data() {
    return {
      monthLabels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sept', 'Oct', 'Nov', 'Dec'],
      dataPoints: [41.1, 1, 15, 16, 23, 41.1, 4, 8, 15, 22, 1, 12],
      dataPointObjects: [{ label: 'N', value: 41.1 }, { label: 'NW', value: 1 }, { label: 'W', value: 15 }, { label: 'SW', value: 16 }, { label: 'S', value: 23 }, { label: 'SE', value: 41.1 }, { label: 'E', value: 4 }, { label: 'NE', value: 8 }],
      dataObj2: [{ label: 'Arsalan Savand', value: 119 }, { label: 'Amir Savand', value: 97 }, { label: 'Arsalan Savand', value: 17 }, { label: 'Alireza Savand', value: 9 }, { label: 'MOJO', value: 9 }, { label: 'User 1 Some Long Name XXX', value: 2 }],
      chartWidth: 450,
      chartHeight: 200,
    };
  },
  created() {
    document.addEventListener('click', () => { this.changeData(); }, false);
  },
  methods: {
    changeData() {
      this.dataPoints = this.dataPoints.map(() => Math.floor(Math.random() * 41) + 1);
    },
  },
};
</script>

<style>
.hello {
  transform: rotate(30 20,40);
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
