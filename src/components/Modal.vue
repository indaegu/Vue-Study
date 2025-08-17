<template>
  <div class="black-bg" @click="$emit('closeModal')">
    <!-- @click.stop : 부모 요소에서의 이벤트를 방지 -->
    <div class="white-bg" @click.stop>
      <button @click="$emit('closeModal')">X</button>
      <img class="item-img" :src="oneRoom.image" alt="대체이미지" />
      <h4>{{ oneRoom.title }}</h4>
      <p>{{ oneRoom.content }}</p>
      <!-- <input @input="month = $event.target.value" /> -->
      <input type="number" v-model="month" />
      <p>{{ `${month}개월 선택함. 가격 : ` + oneRoom.price * month }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalView",
  props: {
    // 여기 선언한 자료형은 틀려도 정상 동작한다. 다만 자바스크립트 특성상 자료형에 혼동이 생길 수 있기 때문에 언급 해주는 느낌
    // props를 통해 부모컴포넌트로 받은 데이터는 수정해서는 안된다. 따라서 만약 해당 데이터를 바꾸고 싶다면 부모컴포넌트로 custom event를 올려 데이터 수정을 요청하면된다
    oneRoom: Object,
  },
  watch: {
    month(newVal) {
      console.log("newVal : " + newVal);
      console.log("typeof newVal : " + typeof newVal);
    },
  },
  data() {
    return {
      month: 1,
    };
  },
  methods: {},
};
</script>
<style></style>
