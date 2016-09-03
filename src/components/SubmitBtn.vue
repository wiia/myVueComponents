<template>
	<div class="submitBtn"
			 :class="{'submitBtn-active': isSubmit, 'submitBtn-success': isSuccess}"
			 v-touch:tap="submit">
			 <span>{{isSuccess ? '发送成功！' : '提交'}}</span>
	</div>
</template>

<script>
export default {
  data () {
    return {
      isSubmit: false,
      isSuccess: false
    }
  },
  props: {
    url: '',
    data: ''
  },
  methods: {
    submit () {
      if (!this.isSubmit) {
        this.isSubmit = !this.isSubmit
        if (window.XMLHttpRequest) {
          let xhr = new window.XMLHttpRequest()
          xhr.onreadystatechange = () => {
            if (xhr.readyState === 4) {
              if (xhr.status === 200) {
                this.isSuccess = !this.isSuccess
              } else {}
            }
          }
          xhr.open('post', this.url)
          xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')
          xhr.send(this.data)
        }
      }
    }
  },
  ready: function () {}
}
</script>

<style lang="less">
		.submitBtn {
			position: absolute;
			width: 280px;
			height: 32px;
			padding: 3px;
			margin: auto;
			left: 0;
			right: 0;
			bottom: 35px;
			transform: translate3d(0, 50%, 0);
			border: 1px solid #d95e61;
			border-radius: 20px;
			font-size: 16px;
			line-height: 1;
			text-align: center;
			color: #d95e61;
			overflow: hidden;
			transition: all .2s;	
			&::before {
				content: '';
				display: block;
				width: 0;
				height: 100%;
				border-radius: 19px;
				background: #d95e61;
				transition: all 1s .5s;
			}
			span {
				position: absolute;
				top: 0;
				bottom: 0;
				height: 16px;
				margin: auto;
				transform: translate3d(-50%, 0, 0);
				transition: all .3s;
			}
		}
		.submitBtn-active {
			height: 6px;
			&::before {
				width: 80%;
			}
			span {
				opacity: 0;
			}
		}
		.submitBtn-success {
			animation: btnLarge .2s 1.3s both;
			&::before {
				width: 100%;
				transition: all .7s;
			}
			span {
				animation: textBack .3s 1.5s both cubic-bezier(.2,.78,.49,1.17);
				color: #fff;
				opacity: 1;
			}
		}
		@keyframes btnLarge {
			from {
				height: 6px;
				// border-width: 1px; 
			}
			to {
				height: 32px;
				// border-width: 2px;
			}
		}
		@keyframes textBack {
			from {
				transform: translate3d(-50%, 0, 0) scale(0, 0); 
			}
			to {
				transform: translate3d(-50%, 0, 0) scale(1, 1);	
			}
	  }
</style>