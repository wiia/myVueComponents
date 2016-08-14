<template>
	<div class="popBanner"
			 :class="{'popBanner-hidden': isHidden}">
		<input type="radio" name="bannerTab" id="bannerTab1" checked>
		<input type="radio" name="bannerTab" id="bannerTab2">
		<input type="radio" name="bannerTab" id="bannerTab3">
		<div class="popBanner-tab">
			<label class="popBanner-tab_item popBanner-tab_item1" for="bannerTab1">主题一</label>
			<label class="popBanner-tab_item popBanner-tab_item2" for="bannerTab2">主题二</label>
			<label class="popBanner-tab_item popBanner-tab_item3" for="bannerTab3">主题三</label>
		</div>
		<div class="popBanner-content">
			<div class="popBanner-con_item popBanner-con_item1"></div>
			<div class="popBanner-con_item popBanner-con_item2"></div>
			<div class="popBanner-con_item popBanner-con_item3"></div>
		</div>
		<div class="popBanner-close"
				 @click="goBack"></div>
	</div>
</template>

<script>
export default {
  data () {
    return {}
  },
  props: {
    isHidden: {
      type: Boolean,
      default: true
    }
  },
  methods: {
    goBack: function () {
      this.isHidden = true
    }
  }
}
</script>

<style lang="less">
	@keyframes wobble-h {
	  0% {
	    transform: none
	  }
	  15% {
	    transform: translate3d(0, -25%, 0) rotate3d(0, 0, 1, -5deg)
	  }
	  30% {
	    transform: translate3d(0, 20%, 0) rotate3d(0, 0, 1, 3deg)
	  }
	  45% {
	    transform: translate3d(0, -15%, 0) rotate3d(0, 0, 1, -3deg)
	  }
	  60% {
	    transform: translate3d(0, 10%, 0) rotate3d(0, 0, 1, 2deg)
	  }
	  75% {
	    transform: translate3d(0, -5%, 0) rotate3d(0, 0, 1, -1deg)
	  }
	  100% {
	    transform: none
	  }
	}
	
	.popBanner {
		position: absolute;
		bottom: 0;
		width: 100%;
		background: rgba(0,0,0,.8);
		transition: all .5s;
		input {
			display: none;
		} 
	}
	.popBanner-hidden {
		transform: translate3d(0,370px,0);
		opacity: 0;
	}	
	.popBanner-tab {
		padding: 0 70px;
		border-bottom: 1px solid rgba(255,255,255,.1);		
	}
	.popBanner-tab_item {
		display: inline-block;
		position: relative;
		width: 60px;
		margin: 0 50px; 
		// border-bottom: 1px solid #5098c6;
		font-size: 20px;
		line-height: 3.5;
		color: rgba(255,255,255,.5);
		text-align: center;
		cursor: pointer;
		transition: all .2s;
		:checked {
			color: rgba(255,255,255,.9);
		}
		&::after {
			content: '';
			position: absolute;
			left: 0;
			right: 0;
			bottom: 0;
			width: 0;
			margin: auto;
			border-bottom: 1px solid #5098c6;
			transition: all .3s;
		}
	}
	#bannerTab1:checked~.popBanner-tab .popBanner-tab_item1,
	#bannerTab2:checked~.popBanner-tab .popBanner-tab_item2,
	#bannerTab3:checked~.popBanner-tab .popBanner-tab_item3,
	.popBanner-tab_item:hover {
		color: rgba(255,255,255,1);
		// text-shadow: 0 0 8px rgba(250,250,250, 0.4);
		&::after {
			width: 100%;
		}
	}
	.popBanner-content {
		height: 300px;
	}
	.popBanner-con_item {
		display: none;
		color: #fff;
	}
	#bannerTab1:checked~.popBanner-content .popBanner-con_item1,
	#bannerTab2:checked~.popBanner-content .popBanner-con_item2,
	#bannerTab3:checked~.popBanner-content .popBanner-con_item3 {
		display: block;
	}
	.popBanner-close {
		position: absolute;
		top: 15px;
		right: 20px;
		width: 24px;
		height: 24px;
		box-sizing: border-box;
		border: 9px #fd7070 solid;
		border-radius: 50px;
		transition: all .2s;
	}
	.popBanner-close:hover {
		// border: 2px #fd7070 solid;
		// opacity: .3;
		cursor: pointer;
		animation: wobble-h .7s;
	}
</style>