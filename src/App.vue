<template>

<div class="subselector">
  <p v-for="sub in subs" :key="sub.name" :class="{'active-sub' : sub.active, 'inactive-sub' : !sub.active}" @click="changeActive(sub)">{{sub.name}}</p>
</div>
<div class="images">
  <div class="sub" v-for="(arr,sub) in imgs" :key="sub">
    <img v-for="img in imgs[sub]" :key="img" :src="img" alt="" rel="preload"/>
  </div>
</div>

</template>

<script>
// import { onMounted } from "vue";
export default {
  name: 'App',
  components: {

  },
  data(){
    return {
      sub: 'gonewild',
      // subs: ['gonewild','gwcouples'],
      subs: [
          {
            name:'nsfwfunny',
            active: true
          },
          {
            name:'bondageblowjobs',
            active:true
          },
          {
            name:'gonewild',
            active: true
          },
          {
            name:'gwcouples',
            active:true
          },
          {
            name:'distension',
            active: true
          },
          {
            name:'sexy',
            active:true
          },
          {
            name:'nsfwart',
            active: true
          },
          {
            name:'xsome',
            active:true
          },
        ],
      // sub: 'natureporn',
      urlbase: 'https://www.reddit.com/r/',
      urlend: '/.json',
      imgs: {},
    }
  },
  methods: {
    async loadImages(){
      let url = this.urlbase + this.sub + this.urlend;
      url = this.urlbase + '+';
      this.subs.forEach((sub,index) => {
        url = url + sub.name;
        if(index < this.subs.length){
          url = url + '+'
        }
      })
      url = url + this.urlend;
      fetch(url).then(res => res.json()).then(d =>{
        d.data.children.forEach(c=>{
          if(this.imgs[c.data.subreddit] == undefined){
              this.imgs[c.data.subreddit] = [];
            }
            this.imgs[c.data.subreddit].push(c.data.url);
          console.log(c.data.url);
        })
      })
      console.log(this.imgs);
    },
    changeActive(sub){
      sub.active = !sub.active;
      console.log(sub, sub.active)
    }
  },
  created(){
    console.log('created');
    this.loadImages();
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
</style>
