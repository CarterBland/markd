<template>
  <div id="app" class="light">
    <icons />
    <navigation />
    <sidebar />
    <main class="content">
       <router-view></router-view>
    </main>
  </div>
</template>

<script>
  import db from './database'

  import Sidebar from './components/Sidebar.vue'
  import Navigation from './components/Navigation.vue'
  import Icons from './components/Icons.vue'

  export default {
    components: {
      Sidebar,
      Navigation,
      Icons
    },
    name: 'App',
    data () {
      return {
        //
      }
    },
    created () {
      this.$store.dispatch('initialLoad');
      db.settings.each((setting) => {
        console.log(setting)
      })
      this.$store.dispatch('initialLoad');
    }
  }
</script>

<style lang="scss">
  @import "./assets/scss/styles.scss";

  #app {
    display: grid;
    grid-template-columns:  320px 1fr;
    grid-template-areas:
      "sidebar navigation"
      "sidebar content";

    @media screen and (max-width: 800px) {
      grid-template-columns: 256px 1fr;
    }
  }

  .content {
    background: var(--content-background);
    display: flex;
    grid-area: content;
    min-height: 100vh;
    overflow: auto;
  }
</style>
