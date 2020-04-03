<template>
  <div v-if="count < 3">
    <p>{{ qChoice.question }}</p>
    <ul>
      <li v-for="o in qChoice.option" :key="o.index">
        <button @click="judgeCorrect(o.correct)">
          {{ o.index }}. {{ o.sentence }}
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
import { countCorrectBus } from "./countCorrectBus"
import qData from "./quiz.json"

export default {
  name: "Question",
  data() {
    return {
      qNumList: [9, 8, 7],
      qList: qData
    }
  },
  props: {
    btnActive: Boolean,
    message: String,
    count: Number
  },
  computed: {
    qChoice() {
      let qChoiceList = []
      for (let n = 0; n < 3; n++) {
        qChoiceList[n] = this.qList[this.qNumList[n]]
      }
      return qChoiceList[this.count]
    }
  },

  methods: {
    //解答の正誤判定+解答ボタンの不活化
    judgeCorrect(c) {
      if (this.btnActive) {
        if (c) {
          this.$emit("update:message", "正解!!!")
          countCorrectBus.$emit("correct-bus")
        } else {
          this.$emit("update:message", "不正解...")
        }
        this.$emit("update:btnActive", false)
      }
    }
  },
  created() {
    //出題する問題を3つ、ランダムに決定
    let a = 0
    for (let i = 0; i < this.qNumList.length; i++) {
      a = Math.floor(Math.random() * this.qList.length)
      this.loop++
      if (this.loop > 30) {
        this.qNumList = [0, 1, 2]
        break
        //問題の重複回避
      } else if (this.qNumList.includes(a)) {
        i--
      } else {
        this.qNumList[i] = a
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  list-style-type: none;
}
</style>
