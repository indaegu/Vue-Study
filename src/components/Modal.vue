<template>
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
</template>

<script>
export default {
  name: "ModalView",
};
</script>
<style></style>
