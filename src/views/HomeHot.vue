<template>
  <div>
    <HomeHotTag />
    <div class="home-hot-question">
      <VQuestion
        :questionData="questionList"
      />
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

import { FETCH_QUESTION_HOT } from '@/store/type/actions'
import HomeHotTag from '@/components/HomeHotTag'

export default {
  name: 'homeHot',
  components: {
    HomeHotTag,
  },
  mounted () {
    this.$store.dispatch(FETCH_QUESTION_HOT,this.hotPage)
    window.addEventListener('scroll',this.handleScroll)
     
    
  },
  computed: {
    ...mapGetters(['hotPage','questionList']),
  },
  methods:{
   handleScroll(){
     let scrollTop = document.documentElement.scrollTop
     let client = document.documentElement.clientHeight
     let scrollHeight = document.documentElement.scrollHeight
     
     if (scrollTop+client >= scrollHeight){
       this.loadMore()
      

     }

   },
   loadMore(){
   
    
   }
  }
}
</script>

<style lang="less" scoped>
.home-hot-question {
  margin-top: 240px;
}
</style>

