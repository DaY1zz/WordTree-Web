<template>
  <div id="container-circle" :class="{hide:data.length==0}"></div>
  <div class="svg" v-if="data.length==0">
    <svg
      t="1621586617012"
      class="icon"
      viewBox="0 0 1146 1024"
      version="1.1"
      xmlns="http://www.w3.org/2000/svg"
      p-id="6384"
      xmlns:xlink="http://www.w3.org/1999/xlink"
      width="150"
      height="150"
    >
      <path
        d="M0 788.389381a507.469027 108.743363 0 1 0 1014.938053 0 507.469027 108.743363 0 1 0-1014.938053 0Z"
        fill="#F3F3F8"
        p-id="6385"
      ></path>
      <path
        d="M321.880354 246.303717h367.915044l174.714337 220.749026s-174.895575 180.151504-352.328496 179.607788-357.584425-181.238938-357.584425-181.238938z"
        fill="#FBFBFD"
        p-id="6386"
      ></path>
      <path
        d="M797.451327 815.575221H217.486726a63.433628 63.433628 0 0 1-63.433629-63.433628V471.221239h166.558584l14.680354 29.360708A81.738761 81.738761 0 0 0 416.849558 579.964602h199.362831a63.614867 63.614867 0 0 0 63.433629-60.533806L711.72531 471.221239h149.159646v280.920354A63.433628 63.433628 0 0 1 797.451327 815.575221z"
        fill="#FBFBFD"
        p-id="6387"
      ></path>
      <path
        d="M797.451327 806.513274a54.371681 54.371681 0 0 0 54.371682-54.371681v-271.858407h-135.385487L688.707965 522.330619a72.495575 72.495575 0 0 1-72.495576 66.69593H416.849558a90.619469 90.619469 0 0 1-90.61947-86.088496l-11.236814-22.654867H163.115044v271.858407a54.371681 54.371681 0 0 0 54.371682 54.371681h579.964601m0 18.123894H217.486726a72.495575 72.495575 0 0 1-72.495576-72.495575v-289.982301h181.238938l18.123894 36.247788a72.495575 72.495575 0 0 0 72.495576 72.495575h199.362831a54.371681 54.371681 0 0 0 54.371682-54.371682l36.247787-54.371681h163.115045v289.982301a72.495575 72.495575 0 0 1-72.495576 72.495575z"
        fill="#E2E2EE"
        p-id="6388"
      ></path>
      <path
        d="M863.059823 467.958938L684.539469 253.734513H330.398584L151.87823 467.958938l-13.774159-11.599292L322.061593 235.610619h370.814867l183.957522 220.749027z"
        fill="#E2E2EE"
        p-id="6389"
      ></path>
    </svg>
    <div class="tips" >
      <span style="color: rgb(200,206,218);font-weight:600;letter-spacing: 3px">暂无单词数据</span>
    </div>
  </div>
</template>

<script>
import { Pie } from "@antv/g2plot";
var piePlot = null;

export default {
  name: "WordDataCircle",
  props: {
    data: [],
  },
  mounted() {
    piePlot = new Pie("container-circle", {
      appendPadding: 10,
      data: this.$props.data,
      angleField: "value",
      colorField: "type",
      radius: 0.8,
      label: {
        type: "outer",
        content: "{name} {percentage}",
      },
      interactions: [{ type: "pie-legend-active" }, { type: "element-active" }],
    });
    piePlot.render();
  },
  updated() {
    piePlot.changeData(this.$props.data);
  },
};
</script>

<style scoped>
#container {
  width: 100%;
  min-height: 400px;
  flex: 1;

}

.svg{
  display: flex;
  align-items: center;
  justify-content: center;
  height:100%;
  flex-direction:column

}

.tips{
  text-align: center;
  margin-right: 0.7vw;
}

.hide{
  display: none;
}
</style>