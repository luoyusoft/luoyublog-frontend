<template>
  <div class="video-content" v-cloak style="margin-bottom: 50px;">
    <iv-row>
      <iv-col :xs="24" :sm="24" :md="24" :lg="17">
        <div style="min-height: 500px" class="layout-left">
          <video-page-header :video="video"></video-page-header>
            <video-player style="height: 100%; width: 100%" class="video-player vjs-custom-skin"
                          ref="videoPlayer"
                          :playsinline="true"
                          :options="videoOptions"
            ></video-player>
          <video-page-content :video="video"></video-page-content>
<!--          <div style="background: white;height: 40px;line-height: 40px;">-->
<!--            <a style="margin-left: 20px" target="_blank" :href="video.videoUrl">下载</a>-->
<!--          </div>-->
          <video-page-footer :postId="video.id"></video-page-footer>
        </div>
      </iv-col>
      <iv-col :xs="0" :sm="0" :md="0" :lg="7">
        <div class="layout-right">
          <recommend :module=1></recommend>
        </div>
      </iv-col>
    </iv-row>
  </div>
</template>

<script>
import { mixin } from '@/utils'
import VideoPageHeader from '@/components/views/Video/VideoPageHeader'
import VideoPageContent from '@/components/views/Video/VideoPageContent'
import VideoPageFooter from '@/components/views/Video/VideoPageFooter'
import Recommend from '@/components/views/Recommend'

export default {
  components: {
    'video-page-header': VideoPageHeader,
    'video-page-content': VideoPageContent,
    'video-page-footer': VideoPageFooter,
    'recommend': Recommend
  },
  mixins: [mixin],
  data () {
    return {
      video: {},
      videoOptions: {
        autoplay: false, // 自动播放
        controls: true, // 用户可以与之交互的控件
        loop: false, // 视频一结束就重新开始
        muted: false, // 默认情况下将使所有音频静音
        aspectRatio: '16:9', // 显示比率
        autoSetup: true, // 阻止播放器为具有data-setup属性的媒体元素运行autoSetup
        fluid: true, // 何时true，Video.js播放器将具有流畅的大小。换句话说，它将扩展以适应其容器。
        preload: 'auto', // 预加载
        notSupportedMessage: '由于视频文件损坏或是该视频使用了你的浏览器不支持的功能不支持播放', // 允许覆盖Video.js无法播放媒体源时显示的默认消息。
        playbackRates: [0.5, 1, 1.5, 2], // 严格大于0的数字数组，其中1表示常速（100％），0.5表示半速（50％），2表示双速（200％）等
        poster: '', // 预览图
        fullscreen: {
          options: {navigationUI: 'hide'}
        },
        // plugins: {
        //   foo: {bar: true},
        //   boo: {baz: false}
        // }, // 这支持在初始化播放器时使用自定义选项自动初始化插件 - 而不是要求您手动初始化它们。
        sources: [
          {
            // src: require('/Users/luoyu/Desktop/天不生我落雨/头条/爱剪辑素材/20191021.mp4'),
            src: '',
            type: 'video/mp4'
          }
        ]
      }
    }
  },
  created () {
    this.getVideo(this.$route.params.videoId)
  },
  methods: {
    getVideo (videoId) {
      this.$http.getVideo(videoId).then((response) => {
        if (response && response.code === 200) {
          this.video = response.data
          this.videoOptions.poster = response.data.cover
          this.videoOptions.sources[0].src = response.data.videoUrl
          this.video.star = Number(this.video.score)
        } else {
          this.$Message.error(response.msg)
        }
      })
    },
    refreshDiectory () {
      /* eslint-disable*/
      new TOC('article-main-page', {
        'level': 5,
        'top': 200,
        'class': 'list',
        'targetId': 'side-toc'
      })
      /* eslint-disable */
      new TocScrollSpy('article-main-page', 'side-toc', {
        'spayLevel': 5,
        'articleMarginTop': 0
      })
    },
    refreshMobileDirectory () {
      /* eslint-disable */
      new TOC('article-main-page', {
        'level': 5,
        'top': 200,
        'class': 'list',
        'targetId': 'sidebar-toc'
      })
      new TocScrollSpy('article-main-page', 'sidebar-toc', {
        'spayLevel': 5,
        'articleMarginTop': 15
      })
    }
  }
}
</script>

<style lang="stylus" rel="stylesheet/stylus">
.video-content
  width auto
  @media only screen and (max-width: 768px)
    margin 5px 5px 10px 5px
  @media screen and (min-width: 768px)
    margin 11px 10px 20px 10px
  @media screen and (min-width: 992px)
    margin 11px 35px 50px 35px
  @media screen and (min-width: 1200px)
    width 1200px
    margin 11px auto 0
  .layout-left, .layout-right
    padding 0
    @media only screen and (max-width: 768px)
      padding 0
    @media screen and (min-width: 768px)
      padding 0
    @media screen and (min-width: 992px)
      padding 0 10px
    @media screen and (min-width: 1200px)
      padding 0 10px

.video-page-header
  text-align left
  padding 25px 5px 10px 5px
  .tags
    margin-bottom 18px
  .title
    font-size 27px
    line-height 33px
    font-weight 500
    color $color-typegraphy-title
    margin-bottom 23px
  .info
    margin-top 10px
    font-size 14px
    line-height 18px
    font-weight 200
    a
      color: #777
      cursor pointer
      &:hover
        color $color-main-primary
        text-decoration underline
    .publish-time
      margin-left 20px
  .operate_info
    text-align right
    font-size 14px
    margin 15px 0
    @media only screen and (max-width: 768px)
      text-align left
    span
      margin-right 10px
      + span
        margin-left 10px
      a
        cursor pointer
        &:hover
          color $color-main-primary
          text-decoration underline
  .abstract
    color $default-desc-color
    border 1px dashed $default-border-color
    background $default-border-color
    @media only screen and (max-width: $responsive-sm)
      padding 8px
      margin-top 8px
      font-size 13px
      line-height 18px
    @media screen and (min-width: $responsive-sm)
      padding 15px
      margin-top 8px
      font-size 14px
      line-height 24px
    @media screen and (min-width: $responsive-md)
      padding 20px
      margin-top 15px
      line-height 28px
    @media screen and (min-width: $responsive-lg)
      padding 20px
      margin-top 15px
      line-height 28px
</style>
