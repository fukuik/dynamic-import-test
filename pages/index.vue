<template>
  <section class="container">
    <div>
      <button @click="clicked" class="button--grey">Dynamic Importでアラート呼び出し</button>
      <h1 class="title">
        test
      </h1>
      <logo/>
      <h2 class="subtitle">
        My astonishing Nuxt.js project
      </h2>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          class="button--green">Documentation</a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="button--grey">GitHub</a>
      </div>
    </div>
  </section>
</template>
<script>
export default {
  components: {
    Logo: () => import('~/components/Logo.vue')
  },
  methods: {
    clicked() {
      import(/* webpackChunkName: "message" */'~/plugins/message.js')
        .then(module => {
          const message = new module.Message();
          message.showAlert();
        });
    }
  }
}

</script>
<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

</style>
