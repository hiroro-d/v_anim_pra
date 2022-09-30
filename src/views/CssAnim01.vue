<template>
  <div class="css__anim01">
    <header-comp></header-comp>
    <main :class="{bgOn: isShow}">
      <section id="mv">
        <button @click="fadeAnim">Fade In/Out</button>
        <transition>
          <h1 class="mv__ttl" v-show="isShow" mode="v-enter">CSS Animation01</h1>
        </transition>
      </section>
    </main>
    <footer-comp></footer-comp>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isShow: false
    }
  },
  methods: {
    fadeAnim() {
      this.isShow = !this.isShow;
    }
  }
}

</script>


<style scoped>
  button {
    position: relative;
  }

  #mv {
    background: url(/public/images/menu13.jpg);
    background-size: cover;
    position: relative;
  }

  #mv::before {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    content: "";
    background-color: white;
    opacity: 1;
    transition: opacity 2500ms ease-out;
  }

  .bgOn #mv::before {
    opacity: 0;
  }

  .mv__ttl {
    font-size: 4.6rem;
    margin: 0.5em 0;
  }

  .v-enter {
    /* フェードインの初期状態 */
    opacity: 0;
  }
  .v-enter-to {
    /* フェードインの終了状態 */
    opacity: 1;
  }
  
  .v-leave {
    /* フェードアウトの初期状態 */
    opacity: 1;
  }
  .v-leave-to {
    /* フェードアウトの終了状態 */
    opacity: 0;
  }

  .v-enter-active {
    /* フェードイン中 */
  }

  .v-leave-active {
    /* フェードアウト中 */
  }

  .v-enter-active, .v-leave-active {
    transition: opacity 5500ms ease-out;
  }
</style>

