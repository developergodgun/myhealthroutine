<template lang="pug">
  div(class="exercise")
    q-checkbox(v-model="check[index]",
              size="xl"
              v-for="(item, index) in exerciseList",
              v-bind:key="item") {{ item }}
</template>

<script>
export default {
  data () {
    return {
      exerciseList: ['스쿼트', '인클라인벤치프레스', '랫풀 다운', '스티프 데드리프트', '플렛 벤치프레스', '시티드로우', '사이드 래터럴 레이즈', '트라이셉션', '벤트 오버 레터럴 레이즈', '크런치'],
      check: [false, false, false, false, false, false, false, false, false, false]
    }
  }
}
</script>

<style lang="scss">
.exercise {
  display: flex;
  flex-direction: column;
}
.q-checkbox {
  border-width: 1px;
  border-style: solid;
}
</style>
