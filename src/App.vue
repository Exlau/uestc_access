<template>
  <div id="app">
    <router-view />
  </div>
</template>
<script>
export default {
  // beforeCreate() {
  //   document
  //     .querySelector("body")
  //     .setAttribute("style", "background-color: #fafafa;");
  // },
};
</script>

<style lang="less">
html,
body {
  width: 100vw;
  height: 100vh;
  background-color: #fafafa;
  margin: 0;
  padding: 0;
}

// #nav {
//   padding: 30px;

//   a {
//     font-weight: bold;
//     color: #2c3e50;

//     &.router-link-exact-active {
//       color: #42b983;
//     }
//   }
// }
</style>
