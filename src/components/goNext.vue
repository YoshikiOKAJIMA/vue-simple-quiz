<template>
  <div>
    <p v-show="message">正誤：{{ message }}</p>
    <button @click="goNext" v-if="message">{{ nextBtn }}</button>
    <Result :countCorrect.sync="countCorrect" :result.sync="result" />
  </div>
</template>

<script>
import Result from "./Result.vue"

export default {
  name: "goNext",
  components: {
    Result
  },
  data() {
    return {
      nextBtn: "次の問題へ",
      result: false,
      countCorrect: 0,
      countQ: 0
    }
  },
  props: {
    btnActive: Boolean,
    message: String,
    count: Number
  },
  methods: {
    //次の問題へボタンの挙動
    goNext() {
      this.countQ++
      this.$emit("update:count", this.countQ)
      this.$emit("update:message", "")
      this.$emit("update:btnActive", true)
      //全問終了後はresultへボタンに
      if (this.countQ === 2) {
        this.nextBtn = "resultへ"
      } else if (this.countQ > 2) {
        this.result = true
        this.$emit("update:btnActive", false)
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
