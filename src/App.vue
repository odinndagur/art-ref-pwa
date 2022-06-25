<template>

<!-- <Suspense> -->
  <HelloWorld></HelloWorld>
<!-- </Suspense> -->
<!-- <div class="subselector">
  <p v-for="sub in subs" :key="sub.name" :class="{'active-sub' : sub.active, 'inactive-sub' : !sub.active}" @click="changeActive(sub)">{{sub.name}}</p>
</div> -->

<!-- <div class="images">
  <div class="sub" v-for="sub in fimgs" :key="sub.name">
    <img v-for="img in sub.imgs" :key="img" :src="img" alt="" rel="preload"/>
  </div>
</div> -->


</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: 'App',
  components: {
    HelloWorld,
},
  data(){
    return {
    }
  },
  methods: {
  },
  created(){
    
  },
  computed: {
    
  },
}
</script>

<style>
html, body {
  width: 70vw;
  margin: auto;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
