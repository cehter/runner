<template>
  <div class="home">
    <h1 class="h1">Your running statistics</h1>
    <div class="widgetList">
      <div class="widget widget--small">
        <div class="widget__header">
          This Week
        </div>
        <div class="circle">20km</div>
      </div>
      <div class="widget widget--medium">
        <div class="widget__header">
          Daily Activity
        </div>
        <BarChart/>
      </div>
    </div>
  </div>
</template>

<script>
import BarChart from "@/components/BarChart.vue";

export default {
  name: "home",
  components: {
    BarChart
  }
}
</script>

<style>
.h1 {
  margin-top: 0;
  margin-bottom: 30px;
}
.widgetList {
  display: flex;
}
.widget {
  padding: 15px;
  border: 1px solid #c8cfd8;
  box-shadow: 0px 3px 3px 0px rgba(226, 228, 231, 1);
  display: flex;
  flex-flow: column;
  justify-content: center;

}
.widget + .widget {
  margin-left: 15px;
}

.widget__header {
  margin-bottom: 15px;
  text-align: left;
}
.widget--small {
  width: 33%;  
  height: 150px;
}

.widget--medium {
  width: 66%;
}

.circle {
  margin: 0 auto;
  width: 100px;
  height: 100px;
  line-height: 100px;
  border-radius: 50%; /* the magic */
  text-align: center;
  color: white;
  font-size: 16px;
  text-transform: uppercase;
  font-weight: 700;
  background-color: #42b983;
}
</style>