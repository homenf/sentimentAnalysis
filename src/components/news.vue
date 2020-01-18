<template>
  <div id="newsTag">
    <div id="title"> {{msg}}</div>
    <div id="sentiment">1 {{sentiment}} </div>
  </div>
</template>

<script>
export default {
   name: 'news',
   props: {
       msg: String
   }
}
</script>

<style scoped>
  #title {
    text-overflow: ellipsis;
    width: 300px;
    background-color: lightgoldenrodyellow;
    font-size: 15px;
    height: 100px;
  }

  #sentiment {
    background-color: aqua;
    width: 100px;
    border-left : 5px solid grey;
    padding: 20px;
    font-size: 40px;
    border-radius: 5px;
  }
  #newsTag {
    margin: 20px auto;
    display: flex;
    justify-content: space-between;
    width: 500px;
  }
</style>