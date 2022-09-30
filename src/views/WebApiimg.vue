<template>
  <div id="main__wrapper">
    <HeaderComp/>
    <main>
      <section id="mv" class="mv__less mv__random-image">
        <div class="copy__wrapper">
          <div class="mv__ttl__wrapper">
            <h2 class="mv__ttl">Random Image</h2>
            <button @click="shuffleArray(posts)" class="btn__random">Random</button>
          </div>
          <transition-group tag="ul" class="img__wrapper">
            <li v-for="post in posts" :key="post"><img :src="post" alt=""></li>
          </transition-group>
        </div>
      </section>
    </main>
    <FooterComp/>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [],
    }
  },
  created() {
    for (let i = 0; i < 20; i++) {
      const imgPath = `https://picsum.photos/id/${i}/400/600`;
      console.log(imgPath)
      this.posts.push(imgPath);
    }
  },
  methods: {
    shuffleArray(array) {
      const cloneArray = [...array];
      cloneArray.reduce((prev, current, index) => {
        let rdmIndex = Math.floor(Math.random() * (index + 1));
        cloneArray[index] = cloneArray[rdmIndex];
        cloneArray[rdmIndex] = current;
        this.posts = cloneArray;
      })
    }
  }
}
</script>

<style scoped>
#mv.mv__random-image .mv__ttl {
  color: #FFF;
  font-size: 6.4rem;
  margin-bottom: 0.2em;
  text-shadow: 1px 1px 3px rgb(0 0 0 / 50%);
}

.copy__wrapper {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.mv__ttl__wrapper {
  top: 30%;
  position: fixed;
  z-index: 5;
  padding: 2em 3em;
  background-color: rgba(50, 113, 85, 0.2);
  border: solid 1px #CCC;
  border-radius: 10px;
  box-shadow: 4px 5px 16px 2px rgb(0 0 0 / 20%);
  margin: 0 14%;
  text-align: center;
  backdrop-filter: blur(10px); /*すりガラス風にする技*/
}



.img__wrapper {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.img__wrapper li {
  flex-grow: 1;
  width: max(calc(25% - 20px), 160x);
  border-radius: 10px;
  overflow: hidden;
  border: solid 1px #ccc;
}

.img__wrapper li img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* トランジショングループ用アニメーション */

.v-enter-active, .v-leave-active, .v-move {
  transition: all 2s;
}

.v-leave-active {
  position: relative;
}

.v-enter, .v-leave-to {
  opacity: 0;
  transform: translateY(-30px);
}

</style>
