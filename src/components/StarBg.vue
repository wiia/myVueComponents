<template>
	<div class="starBg">
		<div class="starBg-star1">
			<img src="../assets/star1.png">
		</div>
		<div class="starBg-star2">
			<img src="../assets/star2.png">
		</div>
		<div class="starBg-star3">
			<img src="../assets/star3.png">
		</div>
		<div class="starBg-clouds"></div>
	</div>
</template>

<style lang="less">
	@keyframes animateBg {
	    0% {
	      background-position: 0 0;
	    }
	    100% {
	      background-position: 1781px 0;
	    }
	}
	@keyframes animateLight {
	    0% {
	      transform: scale3d(.8, .8, 1);
	    }
	    50% {
	      transform: scale3d(.9, .9, .9);
	    }
	    100% {
	      transform: scale3d(.8, .8, 1);
	    }
	}
	@keyframes animateStar {
	    0% {
	      transform: translate3d(0, 0, 0);
	    }
	    50% {
	      transform: translate3d(50px, 0, 0);
	    }
	    100% {
	      transform: translate3d(0, 0, 0);
	    }
	}
	.starBg {
		position: absolute;
		width: 100%;
		height: 100%;
		background: url(http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/QGtchnwXbH7C8r6N.png) center/cover;
	}
	.starBg-star1 {
		position: absolute;
		bottom: 50px;
		right: 140px;
		animation: animateStar 15s linear infinite;
		img {
			width: 500px;
		}
		&::before {
			content: '';
			position: absolute;
			z-index: -1;
			width: 500px;
			height: 500px;
			border-radius: 50%;
			box-shadow: 10px 3px 80px 70px rgba(56, 99, 113, .9);
			tranform: scale3d(.8, .8, 1);
			animation: animateLight 4s linear infinite;
		}
	}
	.starBg-star2 {
		position: absolute;
		top: 50px;
		left: 140px;
		animation: animateStar 15s linear 2s infinite;
		img {
			width: 100px;
		}
		&::before {
			content: '';
			position: absolute;
			z-index: -1;
			width: 100px;
			height: 100px;
			border-radius: 50%;
			box-shadow: -3px -3px 15px 15px rgba(56, 99, 113, .9);
			tranform: scale3d(.8, .8, 1);
			animation: animateLight 4s linear infinite;
		}
	}
	.starBg-star3 {
		position: absolute;
		bottom: 100px;
		left: 490px;
		animation: animateStar 15s linear 4s infinite;
		img {
			width: 160px;
		}
		&::before {
			content: '';
			position: absolute;
			z-index: -1;
			width: 160px;
			height: 160px;
			border-radius: 50%;
			box-shadow: 3px 8px 30px 20px rgba(56, 99, 113, .9);
			tranform: scale3d(.8, .8, 1);
			animation: animateLight 3s linear infinite;
		}
	}
	.starBg-clouds {
		position: absolute; /* stack level为 0 */	
		width: 100%;
		height: 100%;
		background: url(http://facejoin.img-cn-shenzhen.aliyuncs.com/facejoin/aG4Hsm4nedFFf7hG.png);
		animation: animateBg 25s linear infinite;
	}
</style>