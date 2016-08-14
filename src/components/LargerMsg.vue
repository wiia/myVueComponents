<template>
	<div class="largerMsg-wrap"
			 :class="{'largerMsg-wrap-hidden': isHidden}"
			 @click="goBack">
		<div class="largerMsg-panel">
			<div class="largerMsg-avatar" style="background-image: url({{avatar}})"></div>
			<div class="largerMsg-msg">
				<p>{{user}} ：</p>
				<p>{{content}}</p>
			<div>
		</div>     
   </div>
</template>

<script>
export default {
  props: {
    isHidden: {
      type: Boolean,
      default: true
    },
    avatar: '',
    user: '',
    content: ''
  },
  methods: {
    goBack: function () {
      this.isHidden = true
    }
  }
}
</script>

<style lang="less">
.largerMsg-wrap {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background: rgba(0,0,0,.5);
	z-index: 1;
}
.largerMsg-wrap-hidden {
	display: none;
}
.largerMsg-panel {
	width: 300px;
	margin: 200px auto;
	padding: 15px 20px 40px 15px;
	border-radius: 2px;
	color: rgba(255,255,255,.9);
	background: rgba(0,0,0,.8);
	box-shadow:	0 0 8px rgba(0,0,0,.3);
}
.largerMsg-avatar{
	position: absolute;
	width: 40px;
	height: 40px;
	margin: 0 10px 0 0;
	border-radius: 20px;
	vertical-align: middle;
	background: center/cover;
}
.largerMsg-msg {
	margin: 0 0 0 55px;
	font-size: 16px;
	line-height: 2;
	p {
		margin: 0;
	}
}
</style>