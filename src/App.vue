<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <div class="menu">
    <a v-for="(nav, i) in menus" :key="i">{{ nav }}</a>
  </div>
  <!-- 사실 아래 같이 자주 변경되지 않을 데이터는 굳이 바인딩 처리할 필요가 없다 -->
  <!-- {{ logo }} -->
  <h1>뷰동산</h1>

  <div v-for="(price, j) in prices" :key="j">
    <h4>{{ products[j] }}</h4>
    <p>{{ price }} 만원</p>
  </div>
</template>

<script>
var arr1 = [10, 20, 30];
arr1[0];

export default {
  name: "App",
  data() {
    // Vue에선 해당 위치에 데이터를 담아두고 사용한다.
    // 데이터 형태는 object 타입으로 저장한다. ex) {자료이름 : 자료내용}
    return {
      menus: ["Home", "About", "Contact"],
      prices: [60, 100, 200],
      products: ["역삼동원룸", "천호동원룸", "철산동원룸"],
    };
  },
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
</style>
