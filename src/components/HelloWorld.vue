<template>
  <div class="hello">
    <h1>{{ header }}</h1>
    <h2>{{ counter }}</h2>
    <h2>{{ doubleCounter }}</h2>
    <h2>{{ secretCounter }}</h2>
    <button @click="addOne">add 1</button>
  </div>
</template>

<script>
  import { ref, computed, watch } from 'vue'

  export default {
    name: 'HelloWorld',
    props: {
      msg: String
    },  
    computed: {
      secretCounter() {
        return this.counter * 4;
      }
    },
    setup(props) {
      // counter
      const counter = ref(0);
      const doubleCounter = computed(() => {
        return counter.value * 2;
      });
      function addOne() {
        counter.value += 1;
      };      
      watch(counter, (newVal, oldVal) => {
        console.log(newVal);
      });

      // props
      const header = computed(() => {
        return props.msg.replace('Vue.js', 'Vue 3');
      })

      return { counter, doubleCounter, addOne, header};
    },
  }
</script>