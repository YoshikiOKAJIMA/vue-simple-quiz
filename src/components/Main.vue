<template>
  <div>
    <Question
      :btnActive.sync="btnActive"
      :message.sync="message"
      :count.sync="count"
    />
    <goNext
      :btnActive.sync="btnActive"
      :message.sync="message"
      :count.sync="count"
    />
  </div>
</template>

<script>
import Question from "./Question.vue"
import goNext from "./goNext.vue"

export default {
  name: "Main",
  data() {
    return {
      btnActive: true,
      message: "",
      count: 0
    }
  },
  components: {
    Question,
    goNext
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
