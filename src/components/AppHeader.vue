<template>
	<div class="appHeader">
      <h1 class="appHeader-title">ZHAOZHAO</h1>
      <div class="appHeader-menu"
           :class="{'appHeader-menu-active': menu_open}"
           @click="menuOpen">
        <span class="menu-up"></span>
        <span class="menu-cnt"></span>
        <span class="menu-low"></span>
      </div>
      <div class="appHeader-nav">
        <div class="appHeader-nav-item"
             v-for="item of menu_rooter"
             :class="{'appHeader-nav-item-checked': rooter_index === $index}"
             @click="checkMenu($index)">{{item.name}}</div>
      </div>
      <div class="appHeader-search"></div>
    </div>
</template>

<script>
export default {
  data () {
    return {
      menu_open: false,
      rooter_index: -1,
      menu_rooter: [{
        name: '首页',
        url: '',
        is_checked: false
      }, {
        name: '孤独的',
        url: '',
        is_checked: false
      }, {
        name: '米饭',
        url: '',
        is_checked: false
      }, {
        name: '美学',
        url: '',
        is_checked: false
      }, {
        name: '我的',
        url: '',
        is_checked: false
      }]
    }
  },
  methods: {
    menuOpen () {
      this.menu_open = !this.menu_open
    },
    checkMenu (index) {
      this.rooter_index = index
      this.menu_open = !this.menu_open
    }
  }
}
</script>

<style lang="less">
	@menuItem: .4s;
	@menuItemDelay: .9s;

  body {
    margin: 0;
    font-family: -apple-system,Helvetica Neue,Arial,Neo Heiti,sans-serif;
  }
  .appHeader {
    position: relative;
    min-height: 46px;
    padding: 26px 25px 0;
    border-bottom: .5px solid #ccd6d9;
    color: #35383c;
  }
  .appHeader-title {
    margin: 0;
    font-size: 16px;
    line-height: 46px;
    text-align: center;
  }
  .appHeader-menu {
    position: absolute;
    top: ~"calc(50% + 13px)";
    transform: translate3d(0, -50%, 0);
    z-index: 2;
    width: 20px;
    height: 13px;   
  }
  .appHeader-menu span {
      position: absolute;
      height: 1px;
      background: #35383c;
      transition: all .5s ease;
    }
  .menu-up {
    top: 0;
    width: 16px;
  }
  .menu-cnt {
    top: 6px;
    width: 100%;
  }
  .menu-low {
    bottom: 0;
    width: 16px;
  }
  .appHeader-nav {
    position: fixed;
    z-index: 1;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    padding: 90px 20% 0;
    background: rgba(255, 255, 255, .9);
    transition: all .5s ease .4s;
    visibility: hidden;
    opacity: 0;
  }
  .appHeader-nav-item {
    font-size: 12px;
    line-height: 30px;
    transform: translate3d(-20px, 0, 0);
    color: rgba(53, 56, 60, 0.4);
    opacity: 0;
    transition: all @menuItem ease;
  }
  .appHeader-nav-item-checked {
    color: inherit;
    transition: transform @menuItemDelay ease ,
    						opacity @menuItemDelay ease ,
    						color .1s ease;
  }
  .appHeader-menu-active {
  	.menu-up {
  		transform: rotateZ(-35deg)
  		           translate3d(-7px, -5px, 0)
  		           scale(.6, 1);
  		transform-origin: right;
  	}
  	.menu-low{
  	  transform: rotateZ(35deg)
  	             translate3d(-7px, 5px, 0)
  	             scale(.6, 1);
  	  transform-origin: right;
  	}
  	&+.appHeader-nav{
  		transition: all .5s ease;
	    visibility: visible;
	    opacity: 1;
	    .appHeader-nav-item {
	    	transition: all @menuItemDelay ease;
	      transform: translate3d(0, 0, 0);
	      opacity: 1;
	  	}
	  	.appHeader-nav-item-checked {
	  	  transition: transform @menuItem ease,
	  	  						opacity @menuItem ease,
	  	  						color .1s ease;
	  	}
	  }	
  }

</style>