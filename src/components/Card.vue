<template>
  <div>
    <img
      class="item-img"
      :src="oneRoom.image"
      alt="상품대체이미지"
      @click="$emit('openModal', oneRoom.id)"
    />
    <h4 style="cursor: pointer" @click="$emit('openModal', oneRoom.id)">
      {{ oneRoom.title }}
    </h4>
    <p>{{ oneRoom.price }} 만원</p>
    <button @click="$emit('reportUp', oneRoom.id)">허위매물신고</button>
    <span>신고수 : {{ oneRoom.reportCount }}</span>
  </div>
</template>

<script>
export default {
  name: "CardComponent",
  props: {
    // 여기 선언한 자료형은 틀려도 정상 동작한다. 다만 자바스크립트 특성상 자료형에 혼동이 생길 수 있기 때문에 언급 해주는 느낌
    // props를 통해 부모컴포넌트로 받은 데이터는 수정해서는 안된다. 따라서 만약 해당 데이터를 바꾸고 싶다면 부모컴포넌트로 custom event를 올려 데이터 수정을 요청하면된다
    oneRoom: Object,
  },
  data() {
    return {};
  },
  methods: {},
};
</script>
<style></style>
