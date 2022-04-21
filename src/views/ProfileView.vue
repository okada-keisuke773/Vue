<template>
  <div class="profile">
    <transition
      mode="”out-in”"
      name="custom-classes-transition"
      enter-active-class="animated zoomIn"
      leave-active-class="animated zoomOut"
    >
      <div v-if="show" class="main">
        <div class="title">
          <p>Profile</p>
        </div>
        <div class="wrapper-profile">
          <img class="profile-img" src="../assets/it.jpeg" />
          <div class="content">
            <p>岡田佳祐</p>
            <p>KEISUKE OKADA</p>
            <br>
            <p>
              千葉県出身<br>
              2018年ハウスメーカーの営業からIT業界へ転職<br>
              2020年から1年ほど前の会社の社内開発で開発経験<br>
              その後2021年8月にJutJoyへ入社しECサイトの新規開発と並行し、新人の案件の管理、フォローをしています
            </p>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "ProfileView",
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
.profile {
  height: 100%;
  background: linear-gradient(#05FBFF, #1E00FF);
  font-style: italic;
}

.main {
  padding: 30px 20px;
}

.title {
  font-size: 60px;
  padding: 40px;
  margin-top: 30px;
}
.wrapper-profile {
  display: flex;
  padding: 50px;
  justify-content: center;
}
.profile-img {
  width: 250px;
  height: 250px;
  text-align: center;
  margin-right: 50px;
  border-radius: 50%;
}
.content {
  width: 40%;
  padding-left: 20px;
  text-align: left;
  line-height: 1.6;
  color: #5d627b;
  background: white;
  border-top: solid 5px #5d627b;
  box-shadow: 0 3px 5px rgba(0, 0, 0, 0.22);
}
p{
  margin-top: 0;
}

</style>
