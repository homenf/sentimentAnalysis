<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button @click="trymethod" v-bind="btnText">{{btnText}}</button> 
    <div v-if="refreshed" v-bind="refreshTime">Last time refreshed at: {{refreshTime}}</div>
    <div id = "headlines" v-for = 'news in headlines' v-bind:key="news"> <!-- v-bind is binding an attribute to the specific tag-->
      <news v-bind:msg="news"></news>
    </div>
    <ul>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-babel" target="_blank" rel="noopener">babel</a></li>
      <li><a href="https://github.com/vuejs/vue-cli/tree/dev/packages/%40vue/cli-plugin-eslint" target="_blank" rel="noopener">eslint</a></li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
import news from "./news.vue";
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    abc: String,
  },
  data() {
    return {
      headlines: [],
      received: [],
      btnText: 'see what is new',
      refreshTime: '',
      refreshed: false,
      date: new Date() 
    }
  },
  methods: {
    trymethod () {
      this.refreshed = true;
      this.date = new Date();
      this.refreshTime = `${this.date.getHours()}:${this.date.getMinutes()}:${this.date.getSeconds()}`;
      this.btnText = 'refresh the content';
      axios.get('https://www.reddit.com/.json').then(res => {
        // eslint-disable-next-line no-console
        this.getPosts(res);
      })
    },

    getPosts(res) {
      res.data.data.children.forEach(post => {
        // eslint-disable-next-line no-console
        console.log(post);
        this.headlines.push(post.data.title);

        
      })
    }
  },
  components: {
    news
  }

}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
}
a {
  color: #42b983;
}
</style>
