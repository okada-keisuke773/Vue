<template>
  <div class="skills">
    <transition
      mode="”out-in”"
      name="custom-classes-transition"
      enter-active-class="animated zoomIn"
      leave-active-class="animated zoomOut"
    >
      <div v-if="show">
        <div class="title">
          <p>SKILL</p>
        </div>
        <div class="heading">
          <p>Language</p>
        </div>
        <ul class="contents_box">
          <li v-for="skill in list" :key="skill.id">
            <div class="contents">
              <img :src="skill.img" />
              <h3 class="name">{{ skill.name }}</h3>
              <div class="star5_rating" :data-rate="skill.str"></div>
            </div>
          </li>
        </ul>
        <div class="heading">
          <p>Framework/Library</p>
        </div>
        <ul class="contents_box">
          <li v-for="frame in framework" :key="frame.id">
            <div class="contents">
              <img :src="frame.img" />
              <h3 class="name">{{ frame.name }}</h3>
              <div class="star5_rating" :data-rate="frame.str"></div>
            </div>
          </li>
        </ul>
        <div class="heading">
          <p>Others</p>
        </div>
        <ul class="contents_box">
          <li v-for="other in others" :key="other.id">
            <div class="contents">
              <img :src="other.img" />
              <h3 class="name">{{ other.name }}</h3>
              <div class="star5_rating" :data-rate="other.str"></div>
            </div>
          </li>
        </ul>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "SkillView",
  data: function () {
    return {
      show: false,
      list: [
        { id: 1, name: "JavaScript", img: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg', str: '2.5'},
        { id: 2, name: "PHP", img: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg', str: '3'},
        { id: 3, name: "HTML", img: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg', str: '3'},
        { id: 4, name: 'CSS', img: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg', str: '2.5'}
      ],
      framework:[
        {id: 1, name: 'React', img:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg', str: '2'},
        {id: 2, name: 'Vue', img: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg', str: '2'},
        {id: 3, name: 'Jquery', img: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/jquery/jquery-original.svg', str: '2.5'},
        {id: 4, name: 'Laravel', img: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/laravel/laravel-plain.svg', str: '3'},
        {id: 5, name: 'Bootstrap', img: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/bootstrap/bootstrap-original.svg', str: '3'}
      ],
      others:[
        {id: 1, name: 'Git', img:'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg', str: '3.5'},
        {id: 2, name: 'MySQL', img: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg', str: '3'},
        {id: 3, name: 'PostgreSQL', img: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postgresql/postgresql-original.svg', str: '2.5'},
        {id: 4, name: 'Oracle', img: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/oracle/oracle-original.svg', str: '3'},
        {id: 5, name: 'Linux', img: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg', str: '3'},
        {id: 6, name: 'AWS', img: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/amazonwebservices/amazonwebservices-original-wordmark.svg', str: '2'}
      ]
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
.skills {
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
.heading{
  padding: 30px 0;
  margin-left: 35px;
  display: flex;
  font-size: 50px;
}
.heading:first-child{
  padding-bottom: 30px;
}

.contents_box {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  row-gap: 50px;
  column-gap: 30px;
  justify-items: center;
  align-items: center;
}

.name{
  padding: 10px;
}


.star5_rating{
    position: relative;
    z-index: 0;
    display: inline-block;
    white-space: nowrap;
    color: #CCCCCC; /* グレーカラー 自由に設定化 */
    /*font-size: 30px; フォントサイズ 自由に設定化 */
}

.star5_rating:before, .star5_rating:after{
    content: '★★★★★';
}

.star5_rating:after{
    position: absolute;
    z-index: 1;
    top: 0;
    left: 0;
    overflow: hidden;
    white-space: nowrap;
    color: #ffcf32; /* イエローカラー 自由に設定化 */
}

.star5_rating[data-rate="5"]:after{ width: 100%; } /* 星5 */
.star5_rating[data-rate="4.5"]:after{ width: 90%; } /* 星4.5 */
.star5_rating[data-rate="4"]:after{ width: 80%; } /* 星4 */
.star5_rating[data-rate="3.5"]:after{ width: 70%; } /* 星3.5 */
.star5_rating[data-rate="3"]:after{ width: 60%; } /* 星3 */
.star5_rating[data-rate="2.5"]:after{ width: 50%; } /* 星2.5 */
.star5_rating[data-rate="2"]:after{ width: 40%; } /* 星2 */
.star5_rating[data-rate="1.5"]:after{ width: 30%; } /* 星1.5 */
.star5_rating[data-rate="1"]:after{ width: 20%; } /* 星1 */
.star5_rating[data-rate="0.5"]:after{ width: 10%; } /* 星0.5 */
.star5_rating[data-rate="0"]:after{ width: 0%; } /* 星0 */
</style>