<template>
  <div :style="{ width: width }" ref="container" class="pitch-plot-container">
    <div
      class="pitch-plot"
      :style="{
        width: width,
      }"
    >
      <svg
        style="display: block"
        :width="width"
        :viewBox="
          coordSystem.minX +
          ' ' +
          coordSystem.minY +
          ' ' +
          coordSystem.width +
          ' ' +
          coordSystem.height
        "
        preserveAspectRatio="xMidYMid meet"
        :style="{ 'background-color': backgroundColor }"
        ref="svg"
      >
        <template v-for="(p, i) in pitches">
          <circle
            :key="'pitch-' + i"
            v-show="p.isVisible && !p.hidden"
            :class="[
              p.classList,
              { visible: p.isVisible },
              { selected: p.isSelected },
            ]"
            :cx="p.x"
            :cy="scaleY(p.y)"
            :r="p.radius"
            :fill="p.fill"
            :fill-opacity="p.isSelected ? 1 : p.fillOpacity"
            :stroke="p.isSelected ? p.selectedStroke : p.stroke"
            :stroke-opacity="
              p.isSelected ? p.selectedStrokeOpacity : p.strokeOpacity
            "
            :stroke-width="p.isSelected ? p.selectedStrokeWidth : p.strokeWidth"
          />
        </template>
        <rect
          :x="strikezoneCoords.x"
          :y="scaleY(strikezoneCoords.y)"
          :width="strikezoneCoords.width"
          :height="strikezoneCoords.height"
          stroke="#000000"
          :stroke-width="0.02"
          fill-opacity="0"
        ></rect>
      </svg>
    </div>
  </div>
</template>

<script>
/*



Example pitches 
// [
// 		{
//			x: 0, -- REQUIRED - center of ball - in feet
//			y: 2.17, -- REQUIRED -center of ball - in feet
// 			stroke: 'black',-- REQUIRED - outline color
// 			strokeWidth: .01, -- REQUIRED - outline width - in feet
// 			strokeOpacity: 1, -- REQUIRED - outline opacity
// 			selectedStroke: 'gold', -- OPTIONAL - selected outline color
// 			selectedStrokeWidth: 2,	-- OPTIONAL - selected stroke width - in feet
// 			fillOpacity: 1,	-- REQUIRED - fill opacity
// 			fill: 'blue', -- REQUIRED - fill color
// 			radius: 1.5/12, -- REQUIRED - in feet
// 			isSelected: false, -- OPTIONAL
// 			isVisible: true, -- REQUIRED
// 		},
// ]

 */

export default {
  props: {
    width: {
      default: "200px",
      type: String,
    },
    backgroundColor: {
      default: "#DFDFDF",
      type: String,
    },
    pitches: {
      type: Array,
      default: () => [],
    },
  },

  data() {
    const min = 4 / 12;
    const max = 56 / 12;
    const coordSystem = {
      minX: 0 - (max - min) / 2,
      maxX: 0 + (max - min) / 2,
      minY: min,
      maxY: max,
      width: max - min,
      height: max - min,
    };

    return {
      height: null,
      svg: null,

      coordSystem,
      strikezoneCoords: {
        x: -8.5 / 12,
        y: 40 / 12,
        width: 17 / 12,
        height: 20 / 12,
      },
    };
  },

  methods: {
    scaleY(v) {
      return this.coordSystem.maxY - v + this.coordSystem.minY;
    },
  },
};
</script>

<style scoped lang="scss">
</style>
