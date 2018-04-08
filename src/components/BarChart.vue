<template>
    <ul class="bars">
    <li><div style="height: 56px" class="bar"></div><span>M</span></li>
    <li><div style="height: 33px" class="bar"></div><span>T</span></li>
    <li><div style="height: 54px" class="bar"></div><span>W</span></li>
    <li><div style="height: 94px" class="bar"></div><span>T</span></li>
    <li><div style="height: 44px" class="bar"></div><span>F</span></li>
    <li><div style="height: 23px" class="bar"></div><span>S</span></li>
    <li><div style="height: 20px" class="bar"></div><span>S</span></li>
  </ul>
</template>

<script>
export default {
  name: "BarChart",
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.bars {
    display: inline-block;
    height: 200px;
    padding: 0;
    margin: 0;
    }

li {
    display: inline-block;
    width: 55px;
    height: 200px;
    padding: 0;
    margin: 0;
    text-align: center;
    position: relative;
}

.bar {
    display: block;
    width: 50px;
    margin-left: 5px;
    background: #42b983;
    position: absolute;
    bottom: 40px;
}

.bar:hover {
    background: #36a070;
    cursor: pointer;
}

span {
    width: 100%;
    position: absolute;
    bottom: 0;
    left: 0;
    text-align: center;
}
</style>
