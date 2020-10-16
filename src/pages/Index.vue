<template lang="pug">
  q-page
    q-carousel(v-model="slide",
              transition-prev="slide-right",
              transition-next="slide-left",
              animated,
              swipeable,
              navigation,
              padding,
              control-color="primary",
              class="rounded-borders")
      q-carousel-slide(:name="index" v-for="(item, index) in exerciseList" v-bind:key="item")
        div(class="exer name") {{ exerciseList[index].exercise }}
        div(class="sr") - 웜업 -
        div(class="exer kg") {{ exerciseList[index].kg* (1/4) }} kg x 12
        div(class="exer kg") {{ exerciseList[index].kg* (2/4) }} kg x 12
        div(class="exer kg") {{ exerciseList[index].kg* (3/4) }} kg x 12
        div(class="sr") - 본세트 -
        div(class="exer kg") {{ exerciseList[index].kg }} kg
        div(class="exer kg") {{ exerciseList[index].kg }} kg
        div(class="exer count") {{ exerciseList[index].count }}
        div(class="btn")
          <q-btn-toggle class="exer suc" v-model="model[index]" toggle-color="primary" :options="[ { label: '성공', value: 'success' }, { label: '실패', value: 'fail' } ]" />
</template>

<script>
import monday from '../components/mondayExercise'
import wednesday from '../components/wednesdayExercise'
import friday from '../components/fridayExercise'

export default {
  data () {
    return {
      slide: 0,
      model: [
        null, null, null, null, null, null, null, null, null, null
      ],
      exerciseList: [
        { exercise: '스쿼트', kg: 95, count: '8회', val: 0 },
        { exercise: '인클라인', kg: 65, count: '8회', val: 1 },
        { exercise: '랫풀다운', kg: 65, count: '10회', val: 2 },
        { exercise: '스티프데드', kg: 80, count: '10회', val: 3 },
        { exercise: '플랫벤치', kg: 75, count: '8회', val: 4 },
        { exercise: '시티드로우', kg: 70, count: '8회', val: 5 },
        { exercise: '사래레', kg: 12.5, count: '8회', val: 6 },
        { exercise: '트라이셉스 익스텐션', kg: 12.5, count: '12회', val: 7 },
        { exercise: '덤벨 컬', kg: 10, count: '12회', val: 8 },
        { exercise: '밴트 오버 래레', kg: 8, count: '10회', val: 9 }
      ]
    }
  },
  components: { monday, wednesday, friday },
  methods: {
    succesBtn (val) {
      console.log(val)
      this.click = 1
      this.btnColor[val] = ['red', 'yellow']
    },
    failBtn (val) {
      console.log(val)
      this.click = 0
      this.btnColor[val] = ['yellow', 'red']
    }
  }
}
</script>

<style lang="scss">
.q-page {
  width: 100%;
  height: 100vh;
  background-color: red;
}
.q-carousel {
  background-color: yellow;
  height: 100%;
}
.q-carousel-slide {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
.exer {
  width: 100%;
  color: black;
  &.name {
    font-size: 3rem;
  }
  &.kg, &.count {
    font-size: 2rem;
  }
}
.btn {
  width: 100%;
  .q-btn {
    width: 100%;
  }
}
.sr {
  font-size: 2rem;
  margin: 1rem 0;
}
</style>
