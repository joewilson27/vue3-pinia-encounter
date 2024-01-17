<template>
  <div class="home">
    <div class="count">
      {{ count }}
    </div>
    <div class="buttons">
      <button @click="decreaseCount">-</button>
      <button @click="increaseCount">+</button>
    </div>
    <hr />
    <div>
      This counter is: {{ oddOrEven }}
    </div>
  </div>
</template>

<script setup>
// when using setup tag in script, don't need to return variables to expose in template
import { ref, computed } from 'vue'

const count = ref(0)

const increaseCount = () => {
  count.value++
}

const decreaseCount = () => {
  count.value--
}

const oddOrEven = computed(() => {
  if (count.value % 2 === 0) return 'even'
  return 'odd'
})

</script>

<style>
.count {
  font-size: 60px;
  margin: 20px;
}

.buttons button {
  font-size: 40px;
  margin: 20px;
}
</style>