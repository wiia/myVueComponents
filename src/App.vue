<template>
  <star-bg v-if="theme.star"></star-bg>
  <day-bg v-if="theme.day"></day-bg>
  <div id="app">
    <we-show :msg-list="msg_list"
             :show-style="curMsg.showStyle" 
             :show-speed="curMsg.showSpeed"
             :is-scroll="curMsg.isScroll"
             :if-poster="curMsg.ifPoster"
             :poster-content="curMsg.posterContent"></we-show>
  </div>
</template>

<script>
import weShow from './components/WeShow'
import popBanner from './components/PopBanner'
import largerImg from './components/LargerImg'
import starBg from './components/StarBg'

export default {
  data () {
    return {
      theme: {
        star: true,
        day: false
      },
      curMsg: {
        title: '',
        showStyle: 0,
        showSpeed: 5,
        isScroll: 0,
        ifPoster: 1,
        posterContent: ''
      },
      popBanner_hidden: true,
      largerImg_hidden: true,
      msg_list: [{
        wechatIcon: 'http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/YNi4XXkTj4Ps8iXm.png',
        wechatName: '果子',
        postContent: '这么久都不更一次我一定是失踪了'
      }, {
        wechatIcon: 'http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/YNi4XXkTj4Ps8iXm.png',
        wechatName: '车车',
        postContent: '前面果子等等我。。。'
      }, {
        wechatIcon: 'http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/YNi4XXkTj4Ps8iXm.png',
        wechatName: 'yuyuki',
        postContent: '说起失踪我就笑笑不说话'
      }, {
        wechatIcon: 'http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/YNi4XXkTj4Ps8iXm.png',
        wechatName: '青烟凝华',
        postContent: '是不是你们只记得夹了爸爸=='
      }, {
        wechatIcon: 'http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/YNi4XXkTj4Ps8iXm.png',
        wechatName: '人衣',
        postContent: '嗯。。。我没胖'
      }, {
        wechatIcon: 'http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/YNi4XXkTj4Ps8iXm.png',
        wechatName: 'Animenz',
        postContent: '来！a叔给你弹op'
      }]
    }
  },
  components: {
    weShow,
    popBanner,
    largerImg,
    starBg
  },
  methods: {
    popBanner () {
      this.popBanner_hidden = !this.popBanner_hidden
    }
  }
}
</script>

<style lang="less">
@keyframes wobble-v {
    0% {
      transform: none
    }
    15% {
      transform: translate3d(-15%, 0, 0) rotate3d(0, 0, 1, -4deg)
    }
    30% {
      transform: translate3d(15%, 0, 0) rotate3d(0, 0, 1, 2deg)
    }
    45% {
      transform: translate3d(-5%, 0, 0) rotate3d(0, 0, 1, -2deg)
    }
    60% {
      transform: translate3d(5%, 0, 0) rotate3d(0, 0, 1, 1deg)
    }
    75% {
      transform: translate3d(-3%, 0, 0) rotate3d(0, 0, 1, -1deg)
    }
    100% {
      transform: none
    }
  }

html {
  height: 100%;
  overflow: hidden;
  font-family: "Helvetica Neue",Helvetica,Arial,sans-serif;
}
body {
  height: 100%;
  margin: 0;
}
#app {
  padding: 15vh 0;
}
.title {
  position: absolute;
  top: 20px;
  width: 100%;
  font-size: 28px;
  line-height: 4;
  text-align: center;
  color: #fff;
  font-weight: bold;
}
.poster {
  position: absolute;
  top: 80px;
  width: 100%;
  font-size: 28px;
  line-height: 4;
  text-align: center;
  color: #fff;
  font-weight: bold;
}
.menu {
  position: absolute;
  bottom: 30px;
  right: 60px;
  font-family: 'iconfont';
  -webkit-font-smoothing: antialiased;
  -webkit-text-stroke-width: 0.2px;
  span {
    margin: 10px;
    font-size: 20px;
    line-height: 3;
    cursor: pointer;
    color: rgba(255, 255, 255, 0.6);
  }
  span:hover {
    color: rgba(255, 255, 255, 0.9)
  }
}
.qrCode-img {
  position: absolute;
  top: 30px;
  right: 60px;
  width: 80px;
  img {
    width: 100%;
    &:hover {
      cursor: pointer;
      animation: wobble-v .7s;
    }
  }
  &::after {
    content: '扫一扫上墙';
    position: absolute;
    left: 0;
    right: 0;
    font-size: 14px;
    line-height: 25px;
    text-align: center;
    color: #fff;
  } 
}
</style>
