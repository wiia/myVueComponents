<template>
	<div class="largerImg-wrap"
			 :class="{'largerImg-wrap-hidden': isHidden}"
			 v-touch:tap="goBack">
		<img class="largerImg-img" :src="imgSrc">
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
    },
    imgSrc: String
  },
  methods: {
    goBack: function () {
      this.isHidden = true
    }
  },
  ready: function () {
    let self = this
    document.documentElement.addEventListener('touchmove', function (e) {
      if (!self.isHidden) {
        e.preventDefault()
      }
    })
  }
}
</script>

<style lang="less">
	@keyframes larger {
	  0% {
	    transform: scale3d(.9, .9, 1)
	  }
	  100% {
	    transform: scale3d(1, 1, 1)
	  }
	}
	.largerImg-wrap {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: rgba(20,20,20,.95);
		opacity: 1;
		transition: opacity .3s;
	}
	.largerImg-wrap-hidden {
		opacity: 0;
		visibility: hidden;
		.largerImg-img {
			display: none;
		}
	}
	.largerImg-img {
		position: absolute;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;
		max-width: 98%;
		max-height: 98%;
		margin: auto;
		animation: larger .4s;
	}
</style>