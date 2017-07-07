<template lang="pug">
#app
  h2 Wish List
  p
  ul.list-items
    li(v-for="(item,index) in items") {{ item.text }}
      input(
        type="checkbox"
        :id="'item'+ index")
      label(:for="'item'+ index") {{ item }}
        span(
         @click="items.splice(index, 1)"
        ) X
  .add-items 
    input(
      type="text"
      name="item"
      placeholder="wish"
      required,
      v-model="newWishText",
      @keyup.enter="addNewWish"
    )
</template>

<script>
export default {
  data () {
    return {
      newWishText: "",
      items: [],
    };
  },
  // created(){
  //   this.items = JSON.parse(localStorage.getItem("items")) || [] 
  // },
  methods:{
    addNewWish() {
      this.items.push(this.newWishText)
      this.newWishText = ""
    }
  }
};
</script>

<style lang="stylus">
html
  box-sizing: border-box;
  background:url(../static/bg-img.jpg) center no-repeat;
  background-size:cover;
  min-height:100vh;
  display:flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  font-family: Futura,"Trebuchet MS",Arial,sans-serif

svg 
  fill:white
  background: rgba(0,0,0,0.1)
  padding: 20px
  border-radius: 50%
  width:200px
  margin-bottom: 50px

#app 
  max-height: 550px
  background: rgba(255,255,255,0.95)
  box-shadow: 0 0 0 10px rgba(0,0,0,0.1)
  position: relative
  width: 270px
  margin: auto  

h2 
  text-align: center
  margin: 0
  font-weight: 200

.list-items 
  padding: 0 20px
  margin: 0
  text-align: left
  list-style: none
  height: 480px
  overflow: auto

.list-items 
  li 
    border-bottom: 1px solid rgba(0,0,0,0.2);
    padding: 10px 0;
    font-weight: 100;
    display: flex;

.list-items 
  label 
    flex:1
    cursor: pointer

.list-items 
  label 
    > span
        float: right
        display: inline-block
        margin-top: 3px
      
.list-items input 
  display: none

.list-items input + label:before 
  content: '⬜️'
  margin-right: 10px

.list-items input:checked + label:before 
  content: '❤️';

.add-items 
  margin-top: 20px
  padding: 5px
  position: absolute
  bottom: 0
  width: 260px
  background: #EAEFF0
  height: 45px

.add-items input 
  padding:10px
  margin: 5px 0
  outline:0
  border:1px solid rgba(0,0,0,0.1)

</style>