<template>
  <!-- 상단 네비게이션바 -->
  <div class="menu">
    <a href="/" v-for="(nav, i) in menus" :key="i">{{ nav }}</a>
  </div>

  <!-- 모달창 -->
  <!-- v-if 조건이 참일때만 해당 요소를 렌더링 -->
  <div class="black-bg" v-if="modalOpenStatus === true" @click="modalClose()">
    <!-- @click.stop : 부모 요소에서의 이벤트를 방지 -->
    <div class="white-bg" @click.stop>
      <button @click="modalClose()">X</button>
      <img
        class="item-img"
        :src="oneRooms[selectOneRoomIndex].image"
        alt="대체이미지"
      />
      <h4>{{ oneRooms[selectOneRoomIndex].title }}</h4>
      <p>{{ oneRooms[selectOneRoomIndex].content }}</p>
    </div>
  </div>
  <div v-if="1 == 2">참이라면 이게 보이고</div>
  <div v-else-if="1 == 3">아니라면 이게보임</div>
  <div v-else>아니라면 이게보임2</div>

  <!-- 제목 -->
  <h1>뷰동산</h1>

  <!-- 매물 컨텐츠 -->
  <div v-for="(oneRooms, j) in oneRooms" :key="j">
    <img class="item-img" :src="oneRooms.image" alt="" @click="modalOpen(j)" />
    <h4>{{ oneRooms.title }}</h4>
    <p>{{ oneRooms.price }} 만원</p>
    <button @click="reportCountUp(j)">허위매물신고</button>
    <span>신고수 : {{ oneRooms.reportCount }}</span>
  </div>
</template>

<script>
import oneRoomData from "./assets/data.js";
export default {
  name: "App",
  // Vue에선 해당 위치에 데이터를 담아두고 사용한다.
  data() {
    // 데이터 형태는 object 타입으로 저장한다. ex) {자료이름 : 자료내용}
    return {
      oneRooms: oneRoomData,
      modalOpenStatus: false,
      menus: ["Home", "About", "Contact"],
      prices: [60, 100, 200],
      products: ["역삼동원룸", "천호동원룸", "철산동원룸"],
      selectOneRoomIndex: "",
    };
  },
  // Vue에선 해당 위치에서 함수를 선언한다.
  methods: {
    reportCountUp(j) {
      this.oneRooms[j].reportCount++;
    },
    modalOpen(j) {
      this.selectOneRoomIndex = j;
      this.modalOpenStatus = true;
    },
    modalClose() {
      this.modalOpenStatus = false;
    },
  },
  components: {},
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
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
.item-img {
  cursor: pointer;
}
</style>
