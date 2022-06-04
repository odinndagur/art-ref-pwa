<template>

<div class="subselector">
  <p v-for="sub in subs" :key="sub.name" :class="{'active-sub' : sub.active, 'inactive-sub' : !sub.active}" @click="changeActive(sub)">{{sub.name}}</p>
</div>

<div class="images">
  <div class="sub" v-for="sub in fimgs" :key="sub.name">
    <img v-for="img in sub.imgs" :key="img" :src="img" alt="" rel="preload"/>
  </div>
</div>


</template>

<script>
// import { ref } from "vue";

export default {
  // async setup() {
  //   const data = ref(null);
  //   await this.startLoader();
  //   return data;
  // },
  name: 'HelloWorld',
  data(){
    return {
      subs: [
          {
            name:'nsfwfunny',
            active: true,
            imgs: [],
          },
          {
            name:'bondageblowjobs',
            active:true,
            imgs: [],
          },
          {
            name:'gonewild',
            active: true,
            imgs: [],
          },
          {
            name:'gwcouples',
            active:false,
            imgs: [],
          },
          {
            name:'distension',
            active: false,
            imgs: [],
          },
          {
            name:'sexy',
            active:true,
            imgs: [],
          },
          {
            name:'nsfwart',
            active: false,
            imgs: [],
          },
          {
            name:'xsome',
            active:false,
            imgs: [],
          },
          {
            name:'mansex',
            active:true,
            imgs: [],
          },
        ],
      urlbase: 'https://www.reddit.com/r/',
      urlend: '/.json',
    }
  },
  methods: {
    async startLoader(){
      this.subs.forEach(async sub => {
        this.loadImagesFromSub(sub.name).then(s => {
          sub.imgs = s;
          console.log(s);
        })
      })
    },
    async loadImagesFromSub(sub){
      let url = this.urlbase + sub + this.urlend;
      let subImgs = [];
      fetch(url).then(res => res.json()).then(d =>{
        d.data.children.forEach(c=>{
          subImgs.push(c.data.url);
        })
      })
      return subImgs;
    },
    changeActive(sub){
      sub.active = !sub.active;
      console.log(sub, sub.active)
    }
  },
  created(){
    console.log('created');
    // this.loadImages();
    this.startLoader();
  },
  computed: {
    fimgs(){
      return this.subs.filter(sub => {
        return sub.active
      })
    },
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