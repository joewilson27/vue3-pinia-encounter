<template>
  <div class="home">
    <div class="count">
      <!-- {{ count }} -->
      <!-- if you use vuex. if you want to access a property state, you must use 'state' dependencies like this = someStore.state.someProperty -->
      {{ storeCounter.count }}
    </div>
    <div class="buttons">
      <!-- <button @click="decreaseCount">-</button>
      <button @click="increaseCount">+</button> -->

      <!-- in vuex, you use like this = storeCounter.dispatch("counter/decreaseCount") -->
      <button @click="storeCounter.decreaseCount">-</button>
      <button @click="storeCounter.increaseCount">+</button>
    </div>
    <hr />
    <div>
      <!-- This counter is: {{ oddOrEven }} -->

      <!-- in vuex, we need to this instead to use getters = storeCounter.getters.oddOrEven -->
      This counter is: {{ storeCounter.oddOrEven }}
    </div>
    <hr />
    <div>
      <!-- we can use this to edit counter property -->
      <h3>Edit counter:</h3>
      <input 
        type="number"
        v-model="storeCounter.count"
      >
    </div>
  </div>
</template>

<script setup>
// when using setup tag in script, don't need to return variables to expose in template
// import { ref, computed } from 'vue'
import { useCounterStore } from '@/stores/counter'

const storeCounter = useCounterStore()


// no longer need this because we migrated to pinia store
// const count = ref(0)

// const increaseCount = () => {
//   count.value++
// }

// const decreaseCount = () => {
//   count.value--
// }

// const oddOrEven = computed(() => {
//   if (count.value % 2 === 0) return 'even'
//   return 'odd'
// })

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