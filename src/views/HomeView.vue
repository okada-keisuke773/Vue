<template>
  <div class="home">
    <div class="main">
      <transition
        mode="”out-in”"
        name="custom-classes-transition"
        enter-active-class="animated zoomIn"
        leave-active-class="animated zoomOut"
      >
        <p v-if="show" class="text">OKADA Portfolio</p>
      </transition>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeView",
  data: function () {
    return {
      show: false,
    };
  },
  mounted() {
    //コンポーネントがマウントされるタイミングでフラグを書き換え->表示アニメーション
    this.show = true;
  },
  beforeRouteLeave(to, from, next) {
    //vue-routerでの遷移発生イベント時にフラグを書き換え->削除アニメーション
    this.show = false;
    setTimeout(() => {
      //setTimeoutにより、3秒後にページ遷移を実行
      next();
    }, 500);
  },
};
</script>

<style scoped>
.home {
  height: 100%;
  background: linear-gradient(#05FBFF, #1E00FF);
  font-style: italic;
}

.text {
  position: absolute;
  top: 50%;
  left: 50%;
  font-size: 50px;
  color: white;
  -webkit-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  text-align: center; /*一応BOX内の文字も中央寄せ*/
}
</style>
