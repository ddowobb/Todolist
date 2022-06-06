<template>
  <div id="app">
    <TodoApp />
  </div>
</template>

<script>
import TodoApp from "./components/TodoApp.vue";

export default {
  name: "App",
  components: {
    TodoApp,
  },
};
</script>

<style>
body {
  font-family: monospace;
}

/* 卷軸寬度 */
::-webkit-scrollbar {
  width: 9px;
}

/* 卷軸軌道 */
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px rgb(147, 149, 182);
  border-radius: 5px;
}

/* 卷軸樣式 */
::-webkit-scrollbar-thumb {
  background: rgb(105, 84, 133);
  border-radius: 10px;
}

/* 卷軸滑過效果*/
/* ::-webkit-scrollbar-thumb:hover {
                    background: #8e6ab9;
                }  */

/*b1 >>> wrap*/
.wrap {
  height: 560px;
  width: 400px;
  background-image: linear-gradient(rgb(35, 36, 85), rgb(145, 103, 155));
  text-align: center;
  font-size: 15px;
  color: rgb(78, 59, 104);
  border-radius: 20px;
  position: absolute;
  top: 50%;
  left: 50%;
  margin: -300px 0 0 -200px;
}

/*b2 >>> main*/
.main {
  background-color: rgb(255, 255, 255);
  display: inline-block;
  width: 330px;
  height: 440px;
  border-radius: 10px;
  overflow-y: hidden;
}

/*b3 >>> content*/
.content {
  margin: 0 auto;
  max-width: 290px;
  height: 310px;
  color: rgb(78, 59, 104);
  flex: 0%;
  /* overflow: hidden; */
  overflow-y: scroll;
  mask-image: linear-gradient(to top, transparent, black),
    linear-gradient(to left, transparent 17px, black 17px);
  mask-size: 100%;
  mask-position: left bottom;
  -webkit-mask-image: linear-gradient(to top, transparent, black),
    linear-gradient(to left, transparent 17px, black 17px);
  -webkit-mask-size: 100% 20000px;
  -webkit-mask-position: left bottom;
  transition: mask-position 0.5s, -webkit-mask-position 0.5s;
}

.content:hover {
  /* overflow-y: scroll; */
  -webkit-mask-position: left top;
}

.content_text {
  flex-direction: row;
  text-align: left;
  width: 145px;
}

.content_btn {
  flex-direction: row;
  text-align: right;
  width: 145px;
}

.finished_item {
  text-decoration: line-through;
}

input {
  width: 65%;
  float: center;
  height: 30px;
  margin-top: 5px;
  text-align: left;
  text-indent: 5px;
  font-size: 12.6pt;
  border-radius: 7px;
  border: solid 0.5px #ebebeb;
  -webkit-transition: 1s;
  transition: 1s;
}

input[type="text"]:hover {
  box-shadow: 0 0 5pt 0.5pt #d3d3d3;
}

input[type="text"]:focus {
  box-shadow: 0 0 5pt 2pt #d3d3d3;
  outline-width: 0px;
}
</style>
