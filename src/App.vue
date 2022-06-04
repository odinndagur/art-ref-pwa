<template>

<Suspense>
  <HelloWorld></HelloWorld>
</Suspense>
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
// import { onMounted, ref } from "vue";
import HelloWorld from "./components/HelloWorld.vue";

export default {
  // async setup() {
  //   const data = ref(null);
  //   onMounted(() => console.log("mounted"));
  //   data.value = await this.startLoader();
  //   return data;
  // },
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

.images {
  width: 50vw;
  float:right;
}

.subselector {
  width:20vw;
  float:left;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

img {
  width: 400px;
}

.inactive-sub {
  color:gray;
  font-style:italic;
}

.active-sub {
  color: black;
  font-style: bold;
}
</style>
