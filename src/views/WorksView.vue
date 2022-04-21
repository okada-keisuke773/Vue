<template>
  <div class="works">
    <transition
      mode="”out-in”"
      name="custom-classes-transition"
      enter-active-class="animated zoomIn"
      leave-active-class="animated zoomOut"
    >
      <div v-if="show">
        <div class="title">
          <p>Works</p>
        </div>
        <div class="heading">
          <p>Work Experience</p>
        </div>
        <div class="row" v-for="experience in list" :key="experience.id">
          <div class="experience-name">
           <div class="period">
            <p>{{ experience.start }}</p>
            ～
            <p>{{ experience.end }}</p>
            </div>
          </div>
          <div class="content">
            <p class="ex-title">{{ experience.title }}</p>
            <div class="ex-detail">{{ experience.detail }}</div>
            <div class="lang">技術要素</div>
            {{ experience.technical_elements }}
            <div class="process">担当工程</div>
            {{ experience.process }}
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "WorksView",
  data: function () {
    return {
      show: false,

      list: [
        {
          id: 1,
          start: "2021年8月",
          end: "現在",
          title: "SFCCを利用したWEBアプリケーション開発",
          detail:
            "既存WEBアプリケーションをSFCCへ移行。PLSQLや使用したプロシージャの作成や、PHPでのAPIの開発",
          technical_elements:
            "PHP、Smarty、Oracle(PLSQL)、GitHub",
          process:
            "詳細設計、コーディング、単体テスト、結合テスト、総合テスト"
        },
        {
          id: 2,
          start: "2021年1月",
          end: "2021年5月",
          title: "社内向けポータルサイト",
          detail:
            "オープンソースを使用した社内向けポータルサイトの開発",
          technical_elements:
            "JavaScript、React、MongoDB(PLSQL)、Git、AWS",
          process:
            "詳細設計、コーディング、単体テスト、結合テスト"
        },
        {
          id: 3,
          start: "2020年10月",
          end: "2021年5月",
          title: "営業管理システム",
          detail:
            "営業管理システムの新規開発",
          technical_elements:
            "PHP、Laravel、JavaScript、Jquery、PostgreSQL、Git、AWS",
          process:
            "要件定義、基本設計、詳細設計、コーディング、単体テスト、結合テスト"
        },
      ],
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
.works {
  padding: 30px;
  background: linear-gradient(#05FBFF, #1E00FF);
  font-style: italic;
  flex-wrap: wrap;
}

.title {
  font-size: 60px;
  padding: 40px;
  margin-top: 30px;
}

.heading {
  padding: 30px 0;
  margin-left: 35px;
  display: flex;
  font-size: 50px;
}
.heading:first-child {
  padding-bottom: 30px;
}

.row {
  display: flex;
  padding: 25px;
  justify-content: center;
}


.period{
padding-top: 35px;
}

.experience-name {
  width: 20%;
  text-align: center;
  line-height: 1.6;
  color: #5d627b;
  background: white;
  border-top: solid 5px #5d627b;
  border-right: solid 2px #5d627b;
}

.content {
  width: 50%;
  padding-left: 20px;
  text-align: left;
  line-height: 1.6;
  color: #5d627b;
  background: white;
  border-top: solid 5px #5d627b;
}

.ex-title {
  font-size: 20px;
  font-weight: 600;
}
.ex-detail {
  font-size: 17px;
}

.lang process{
 font-size: 15px;
 padding-top: 5px;
}
</style>
