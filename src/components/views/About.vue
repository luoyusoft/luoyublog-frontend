<template>
  <div class="about">
    <img class="background" src="../../assets/background.jpg" alt="">
    <a :href="'/'"><img class="avatar" src="../../assets/jinhx-min.jpg" alt=""></a>
    <p class="name">站长</p>
<!--    <p class="desc">看山是山！看山不是山！看山还是山！</p>-->
    <iv-modal :title="'微信扫码，或搜索「码农要充电」关注'" v-model="showGZH" :footer-hide="true" :scrollable="true">
      <img src="../../assets/icon/gongzhonghao.png" alt="" title="码农要充电">
    </iv-modal>
<!--    <iv-drawer title="微信扫码，或搜索「码农要充电」关注" placement="right" width="330px" v-model="showGZH">-->
<!--      <img src="../../assets/icon/gongzhonghao.png" alt="" title="码农要充电" style="width: 300px; height: 300px; text-align: center">-->
<!--    </iv-drawer>-->
    <ul class="social">
      <li><a @click="showGZH = true" style="font-size: 5px"><img src="../../assets/icon/gongzhonghao.png" alt="" title="码农要充电" style="padding-bottom: 5px">公众号</a></li>
      <li><a href="https://www.jianshu.com/u/ede51a29ab7e" target="_blank" style="font-size: 10px"><img src="../../assets/icon/jianshu.png" alt="" title="简书" style="padding-bottom: 5px">简书</a></li>
      <li><a href="https://github.com/Jinhx128" target="_blank" style="font-size: 10px"><img src="../../assets/icon/github.png" alt="" title="GitHub" style="padding-bottom: 5px">GitHub</a></li>
      <li><a href="https://weibo.com/u/1836134790?topnav=1&wvr=6&topsug=1&is_all=1" target="_blank" style="font-size: 10px"><img src="../../assets/icon/weibo.png" alt="" title="微博" style="padding-bottom: 5px">微博</a></li>
    </ul>
<!--    <div class="line"></div>-->
<!--    <h4>技能值</h4>-->
<!--    <div class="progresses">-->
<!--      <iv-row :gutter="20">-->
<!--        <iv-col :span="6">-->
<!--          <p class="title">Java</p>-->
<!--        </iv-col>-->
<!--        <iv-col :span="18">-->
<!--          <iv-progress status="normal" :hide-info="true" :stroke-width="8" :percent="60" class="bar"></iv-progress>-->
<!--        </iv-col>-->
<!--      </iv-row>-->
<!--      <iv-row :gutter="20">-->
<!--        <iv-col :span="6">-->
<!--          <p class="title">Vue</p>-->
<!--        </iv-col>-->
<!--        <iv-col :span="18">-->
<!--          <iv-progress status="wrong" :hide-info="true" :stroke-width="8" :percent="40" class="bar"></iv-progress>-->
<!--        </iv-col>-->
<!--      </iv-row>-->
<!--      <iv-row :gutter="20">-->
<!--        <iv-col :span="6">-->
<!--          <p class="title">Go</p>-->
<!--        </iv-col>-->
<!--        <iv-col :span="18">-->
<!--          <iv-progress status="success" :hide-info="true" :stroke-width="8" :percent="10" class="bar"></iv-progress>-->
<!--        </iv-col>-->
<!--      </iv-row>-->
<!--      <iv-row :gutter="20">-->
<!--        <iv-col :span="6">-->
<!--          <p class="title">Cloud</p>-->
<!--        </iv-col>-->
<!--        <iv-col :span="18">-->
<!--          <iv-progress status="active" :hide-info="true" :stroke-width="8" :percent="30" class="bar"></iv-progress>-->
<!--        </iv-col>-->
<!--      </iv-row>-->
<!--    </div>-->
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  data () {
    return {
      showGZH: false
    }
  }
}
</script>

<style lang="stylus" rel="stylesheet/stylus" scoped>
  @import "../../common/stylus/theme.styl";

  .about
    position relative
    text-align center
    //border 1px solid $color-border
    padding-bottom 20px
    background #393a3d
    border-radius $border-radius
    img.background
      position absolute
      top 0
      left 0
      right 0
      width 100%
      height 125px
      z-index 1
    img.avatar
      position relative
      margin 75px auto 15px
      width 100px
      height 100px
      border 5px solid $color-gradually-gray-91
      border-radius 50%
      z-index 9
    .name
      font-size 20px
      color $color-typegraphy-title
      line-height 30px
      font-weight 700
    .desc
      font-size 15px
      color $color-secondary-info
      line-height 30px
      font-weight 100
    .social
      text-align center
      padding 0 20px
      margin-top 25px
      > li
        padding 8px
        display inline-block
        a
          display block
          width: 40px
          height: 35px
          margin: auto
          img
            width 100%
    .line
      height 1px
      background-color $color-gradually-gray-91
      margin 10px 20px
    h4
      font-size 19px
      margin 30px 0 20px
      font-weight 600
    .progresses
      padding 0 20px
      p.title
        height 38px
        line-height 38px
        text-align right
      .bar
        margin 10px 0
</style>
