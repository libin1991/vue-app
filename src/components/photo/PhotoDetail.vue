<template>
  <div class="photo">
    <common-header></common-header>
    <v-touch @swipeleft="next" @swiperight="prev" class="photo-box" :style="bgStyle"></v-touch>
  </div>
</template>

<script>

  import CommonHeader from '../common/CommonHeader'

export default {
  data() {
    return {
      index:this.$route.params.index,
    }
  },
  components:{
    CommonHeader,
  },
  mounted(){
    this.$store.dispatch('changeTitle',['photo','rgb(63, 81, 181)','<',false]);
  },
  computed:{
    bgStyle(){
      return {
        background: "url('" + this.$store.state.photoList[this.index].src + "') no-repeat center / contain #000"
      }
    }
  },
  methods:{
    next(){
        this.index = (this.index+1)%58;
    },
    prev(){
        this.index = (this.index+57)%58;
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

  @import "../../assets/css/reset.css";
  .photo-box{
    position: absolute;
    top:1rem;
    bottom: 0;
    width: 100%;
  }


</style>
