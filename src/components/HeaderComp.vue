<template>
  <header>
    <div class="container">
      <h1 class="logo"><a href="#"><img src="/images/logo.png" alt="Cafe Du Ando"></a></h1>
      <div class="btn__gnav">
        <input type="checkbox" id="btn__gnav--check" v-model="isActive">
        <label for="btn__gnav--check">
          <svg id="btn__gnav__ic" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-list" viewBox="0 0 16 16">
            <path fill-rule="evenodd" d="M2.5 12a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5z"/>
          </svg>
        </label>
        <label for="btn__gnav--check" id="btn_close"></label>
        <nav id="gnav" @click="menuClose">
          <ul>
            <li><router-link  to="/CssAnim01/">CssAnim01</router-link></li>
            <li><router-link  to="/CssAnim02/">CssAnim02</router-link></li>
            <li><router-link  to="/WebApiimg/">Random Image</router-link></li>
          </ul>
        </nav>
      </div><!--btn__gnav-->
    </div><!-- /.container -->
  </header>
</template>

<script>
export default {
  data() {
    return {
      isActive: false,
    }
  },
  methods: {
    menuClose() {
      this.isActive = !this.isActive;
    }
  }
}
</script>
