<template>
  <div>
    <section>
      <h2>{{ quiz[0] }}</h2>
      <ul>
        <li
          :class="{
            'custom-current-content': isCurrent(0),
            'custom-wrong-content': isWrong(0),
          }"
          class="cursor-pointer"
          @click="checkAnswer(0)"
        >
          {{ quiz[1] }}
        </li>
        <li
          :class="{
            'custom-current-content': isCurrent(1),
            'custom-wrong-content': isWrong(1),
          }"
          class="cursor-pointer"
          @click="checkAnswer(1)"
        >
          {{ quiz[2] }}
        </li>
        <li
          :class="{
            'custom-current-content': isCurrent(2),
            'custom-wrong-content': isWrong(2),
          }"
          class="cursor-pointer"
          @click="checkAnswer(2)"
        >
          {{ quiz[3] }}
        </li>
      </ul>
    </section>
  </div>
</template>
<script setup>
defineProps(["quiz"]);
import { ref } from "vue";
// 問題文, 選択肢, 選択肢, 選択肢, 正解(0, 1, 2)
const quiz = ref(
  ["1の正解は？", "選択肢 A", "選択肢 B", "選択肢 C", 0],
  ["2の正解は？", "選択肢 A", "選択肢 B", "選択肢 C", 1],
  ["3の正解は？", "選択肢 A", "選択肢 B", "選択肢 C", 2]
);
const selectOption = ref();
const checkAnswer = (index) => {
  // if (quiz.value[4] === index) {
  //   selectOption.value = index;
  // } else {
  //   selectOption.value = -1;
  // }
  selectOption.value = index;
};
const isCurrent = (index) => {
  return selectOption.value === index && quiz.value[4] === index;
};
const isWrong = (index) => {
  return selectOption.value === index && quiz.value[4] !== index;
};
</script>
