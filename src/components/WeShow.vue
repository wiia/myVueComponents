<template>
	<div class="weShow-box"
			 v-for="item of msg_box">
		<div class="weShow-msg"
			 	 v-for="sub_item of item"
			 	 track-by="$index"
			 	 @click="largerMsg($parent.$index, $index)"
         :style="{animationDuration: showSpeed * 3 + 's'}">
     	<span class="msg-avatar" :style="{backgroundImage: 'url(' + sub_item.wechatIcon + ')'}"></span>
     	<span class="msg-ctn">{{sub_item.wechatName}}：{{sub_item.postContent}}</span>
  	</div>
	</div>
	<larger-msg :is-hidden.sync="largerMsg_hidden.is_hidden"
              :avatar="largerMsg_hidden.avatar"
							:user="largerMsg_hidden.user"
							:content="largerMsg_hidden.content"></larger-msg>
</template>

<script>
import largerMsg from './LargerMsg'

export default {
  data () {
    return {
      largerMsg_hidden: {
        is_hidden: true,
        avatar: '',
        user: '',
        content: ''
      },
      cur: -1,
      msg_box: [[], [], [], [], [], [], []]
    }
  },
  props: {
    msgList: [],
    showStyle: 0,
    showSpeed: '5',
    isScroll: 1,
    ifPoster: 1,
    posterContent: ''
  },
  components: {
    largerMsg
  },
  methods: {
    largerMsg (parent, index) {
      this.largerMsg_hidden.is_hidden = !this.largerMsg_hidden.is_hidden
      this.largerMsg_hidden.avatar = this.msg_box[parent][index].wechatIcon
      this.largerMsg_hidden.user = this.msg_box[parent][index].wechatName
      this.largerMsg_hidden.content = this.msg_box[parent][index].postContent
    },
    addMsg () {
      if (this.cur < this.msgList.length - 1) {
        var road = Math.floor(Math.random() * 6.9)
        this.msg_box[road].push(this.msgList[this.cur + 1])
        this.cur++
      } else if (this.isScroll) {
        this.cur = -1
      }
    },
    delMsg () {
      for (var i = 0; i < this.msg_box.length; i++) {
        if (this.msg_box[i].length > 20) {
          for (var j = 0; j < 5; j++) {
            this.msg_box[i].shift()
          }
        }
      }
    }
  },
  ready () {
    setInterval(this.addMsg, 2000)
    setInterval(this.delMsg, 15000)
  }
}
</script>

<style>
@keyframes croScreen {
 0%{
 	transform: translate3d(100vw,0,0);
 }
 100%{
 	transform: translate3d(-200vw,0,0);
 }
}

.weShow-box{
	position: relative;
	height: 10vh;
}
.weShow-msg {
	position: absolute;
	padding: 0 20px 0 15px;
	margin: 0 20px 0 0;
	border-radius: 4px;
	font-size: 0;
	background: rgba(50,50,50,.25);
	box-shadow:	inset 0 0 50px 1px rgba(250,245,255,.3),
							inset 0 0 60px rgba(50,50,50,.1),
							0 0 8px rgba(0,0,0,.3);
	cursor: pointer;
	animation: croScreen linear forwards;
}
.weShow-msg:hover {
	box-shadow:	inset 0 0 50px rgba(250,245,255,.3),
							inset 0 0 60px rgba(50,50,50,.1),
							0 0 8px 2px rgba(0,0,0,.3);
	animation-play-state: paused;
	z-index: 1;
}
.msg-avatar {
	display: inline-block;
	width: 40px;
	height: 40px;
	margin: 0 10px 0 0;
	border-radius: 20px;
	vertical-align: middle;
	background: url('../assets/bg.png') center/cover;
}
.msg-ctn {
	font-size: 20px;
	line-height: 2.5;
	vertical-align: middle;
	color: rgba(255,255,255,.9);
}
</style>