<template>
  <el-carousel ref="carouselOut" class="carouselOut" :interval="4000" >
    <el-carousel-item v-for="(item,index) in result" :key="index">
      <img v-if="index == 0" @load="hh"  ref="img" :src="item.src" alt="刷新看看">
      <img v-if="index != 0"  ref="img" :src="item.src" alt="刷新看看">
    </el-carousel-item>
  </el-carousel>
</template>

<script>

export default{
  data () {
    return {
      result: [{'src': require('../assets/imgs/bg3.jpg')}, {'src': require('../assets/imgs/bg4.jpg')}, {'src': require('../assets/imgs/bg7.jpg')}]
    }
  },
  mounted () {
    window.addEventListener('resize', () => {
      this.resizeHeight()
    })
  },
  methods: {
    resizeHeight () { // 窗口变化的时候重新计算轮播图高度
      const imgHeight = this.$refs.img[0].height
      this.$refs.carouselOut.$el.style.height = `${imgHeight + 20}px`
    },
    hh () {
      this.resizeHeight()
    }
  },
  computed: {

  },
  watch: {

  }
}

</script>

<style lang="stylus" scoped>
.el-carousel__item h3
  color: #475669;
  font-size: 14px;
  opacity: 0.75;
  margin: 0;
.el-carousel__item:nth-child(2n)
  background-color: #99a9bf;
.el-carousel__item:nth-child(2n+1)
  background-color: #d3dce6;
img
  width 100%
  height 100px
  @media(max-width:350px)
    height 100px
  @media(min-width:360px)
    height 130px
  @media(min-width:400px)
    height 160px
</style>
