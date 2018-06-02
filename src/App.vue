<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <div class="header">
      <div class="header-content">
        <div class="title">
          <h1>JUNE</h1>
          <span>Alzheimer's & Brain Awareness Month</span>
        </div>
        <div class="content">
          Go purple and raise awareness this June.
          <a href="https://twitter.com/alzassociation" target="_blank"><i class="fab fa-twitter"></i></a>
        </div>
      </div>
    </div>
    <Frame/>
  </div>
</template>

<script>
import Frame from './components/Frame.vue';

export default {
  name: 'app',
  components: {
    Frame
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.header {
  height: 40vh;
  background-color: #4a0d66;
  color: #fff;
}

.header-content {
  padding-top: 80px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.header-content h1 {
  font-size: 40px;
  font-weight: bold;
}

.header-content .title {
  display: flex;
  justify-content: center;
  align-items: center;
}

.header-content .title > h1 {
  margin-right: 20px;
  margin-left: 40px;
}

.header-content .content {
  padding-top: 20px;
  text-align: left;
}

.header-content .content a {
  color: #f0d5f5;
}

.header-content .content a .fa-twitter {
  transition: all 0.2s ease-in;
}
.header-content .content a:hover >
.fa-twitter {
  color: #fff;
}

</style>
