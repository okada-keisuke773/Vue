<template>
  <header>
    <ul class="header-list" data-v-header>
      <li class="header-link"><router-link to="/">Home</router-link></li>
      <li class="header-link"><router-link to="/profile">Profile</router-link></li>
      <li class="header-link"><router-link to="/skill">Skill</router-link></li>
      <li class="header-link"><router-link to="/works">Works</router-link></li>
    </ul>
  </header>
</template>

<script>
export default {};
</script>

<style scoped>

header {
  position: fixed;
  width: 100%;
  padding: 30px;
  z-index: 10;
}

header a {
  font-weight: bold;
  color: #2c3e50;
}

header a.router-link-exact-active {
  color: white;
}

ul.header-list[data-v-header] {
  list-style-type: none;
  text-align: right;
  margin-right: 80px;
}
.header {
  padding: 30px;
}

ul.header-list[data-v-header] > li:not(:first-child) {
  margin-left: 50px;
}

li.header-link {
  width: 100%;
  color: #333;
  display: inline;
}
</style>