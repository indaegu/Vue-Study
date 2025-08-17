<template>
  <!-- 상단 네비게이션바 -->
  <div class="menu">
    <a href="/" v-for="(nav, i) in menus" :key="i">{{ nav }}</a>
  </div>

  <!-- 모달창 -->
  <!-- v-if 조건이 참일때만 해당 요소를 렌더링 -->
  <!-- 모달창 -->
  <Transition name="fade">
    <!-- Transition태그는 단 하나의 루트노드가 있을때 정상적으로 사용 가능함. 
     따라서 div 태그를 지우면 Modal 컴포넌트 내부의 template 태그와 충돌이 발생 -->
    <div v-if="modalOpenStatus === true">
      <Modal
        @closeModal="modalOpenStatus = false"
        :oneRoom="oneRooms[selectOneRoomIndex]"
      />
    </div>
  </Transition>

  <div v-if="1 == 2">참이라면 이게 보이고</div>
  <div v-else-if="1 == 3">아니라면 이게보임</div>
  <div v-else>아니라면 이게보임2</div>

  <!-- 제목 -->
  <h1>뷰동산</h1>
  <!-- 매물 컨텐츠 -->
  <Card
    @openModal="(modalOpenStatus = true), (selectOneRoomIndex = $event)"
    @reportUp="oneRooms[$event].reportCount++"
    :oneRoom="oneRoom"
    v-for="(oneRoom, j) in oneRooms"
    :key="j"
  />

  <!-- <div v-for="(oneRooms, j) in oneRooms" :key="j">
    <img class="item-img" :src="oneRooms.image" alt="" @click="modalOpen(j)" />
    <h4>{{ oneRooms.title }}</h4>
    <p>{{ oneRooms.price }} 만원</p>
    <button @click="reportCountUp(j)">허위매물신고</button>
    <span>신고수 : {{ oneRooms.reportCount }}</span>
  </div> -->
  <!-- 자식컴포넌트 -->
  <Discount v-bind="obj" /> <Discount />
</template>

<script>
import oneRoomData from "./assets/data.js";
import Discount from "./Discount.vue";
import Modal from "./components/Modal.vue";
import Card from "./components/Card.vue";

export default {
  name: "App",
  components: { Discount, Modal, Card },
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
      obj: { id: 1, name: "Room1" },
    };
  },
  // Vue에선 해당 위치에서 함수를 선언한다.
  methods: {},
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
/* 애니메이션 */
.start {
  opacity: 1;
  transition: all 2ms;
}
.end {
  opacity: 0;
}
/* Vue transition 클래스 네이밍 규칙: name-enter-active, name-leave-active 등 */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease; /* 0.5초 동안 서서히 */
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0; /* 시작은 안 보이게 */
}
.fade-enter-to,
.fade-leave-from {
  opacity: 1; /* 끝은 보이게 */
}
</style>
