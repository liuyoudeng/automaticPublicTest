<!--
 * @Date: 2021-09-10 14:40:50
 * @LastEditors: lyd
 * @LastEditTime: 2021-09-10 17:47:34
 * @Description: 布局组件
-->
<template>
  <div>
    <!-- 顶部 -->
     <nav class="navbar navbar-light">
      <div class="container">
        <nuxt-link class="nav-brand" to="/">Home</nuxt-link>
        <ul class="nav navbar-nav pull-xs-right">
          <li class="nav-item">
            <!-- Add "active" class when you're on that page" -->
            <!-- <a class="nav-link active" href="">Home</a> -->
            <!-- exact精确匹配 -->
            <nuxt-link 
            class="nav-link" 
            to="/"
            exact
            >Home</nuxt-link> 
          </li>
          <template v-if="user">
            <li class="nav-item">
              <nuxt-link 
              class="nav-link" 
              to="/editor"
              >
              <i class="ion-compose"></i>&nbsp;New Post</nuxt-link>
            </li>
            <li class="nav-item">
                <nuxt-link
                  class="nav-link"
                  to="/settings"
                >
                  <i class="ion-gear-a"></i>&nbsp;Settings
                </nuxt-link>
            </li>
            <li class="nav-item">
                <nuxt-link class="nav-link" :to="`/profile/${user.username}`">
                  <img
                    class="user-pic"
                    :src="user.image"
                  >
                  {{ user.username }}
                </nuxt-link>
            </li>
          </template>
          <template v-else>
            <li class="nav-item">
                <nuxt-link  class="nav-link" to="/login">Sign in </nuxt-link>
            </li>
            <li class="nav-item">
                <nuxt-link  class="nav-link" to="/register">Sign up </nuxt-link>
            </li>
          </template>

        </ul>
      </div>
    </nav>
    <!-- 子路由 -->
    <nuxt-child/>

    <!-- 底部 -->
    <footer>
      <div class="container">
        <a href="/" class="logo-font">conduit</a>
        <span class="attribution">
          An interactive learning project from <a href="https://thinkster.io">Thinkster</a>. Code &amp; design licensed under MIT.
        </span>
      </div>
    </footer>
  </div>
</template> <script>
import { mapState } from 'vuex'
export default {
   name: "LayoutIndex" ,
   computed: {
     ...mapState(['user'])
   }

};
</script>
 <style>
</style>
