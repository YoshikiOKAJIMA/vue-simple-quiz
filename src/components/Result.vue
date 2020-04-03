<template>
  <div v-if="result">
    全問終了です。貴殿の正解数は{{ countCorrect }}です。お疲れ様でした。
  </div>
</template>

<script>
import { countCorrectBus } from "./countCorrectBus"

export default {
  name: "Result",
  data() {
    return {
      countCorrect: 0
    }
  },
  props: {
    result: Boolean
  },
  //以下試行錯誤の産物のため大丈夫かは不明。
  created() {
    countCorrectBus.$on("correct-bus", () => {
      countCorrectBus.countBus++
      return (this.countCorrect = countCorrectBus.countBus)
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
