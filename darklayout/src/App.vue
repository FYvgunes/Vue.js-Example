<template>
  <div id="app" :class="{ 'theme-dark': nightmode }">
    <transition name="fade" mode="out-in"
      ><div class="container">
        <nav>
          <i
            class="fas fa-sun sun-icon"
            v-if="nightmode"
            @click="nightmode = !nightmode"
          ></i>
          <i
            class="fas fa-moon dark-icon"
            v-else
            @click="nightmode = !nightmode"
          ></i>
        </nav>
        <article>
          <img src="./assets/pexels-domianick-4451823.jpg" alt="" />
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic
            reiciendis quis aliquam saepe est accusantium corporis recusandae
            nostrum, aut, atque, minima sit maxime cum quisquam.
          </p>
        </article>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      nightmode: false
    };
  },
  watch: {
    nightmode() {
      localStorage.setItem("nightmode", JSON.stringify(this.nightmode));
    }
  },
  created() {
    this.nightmode = JSON.parse(localStorage.getItem("nightmode"));
  }
};
</script>

<style lang="scss">
@import url("https://use.fontawesome.com/releases/v5.8.1/css/all.css");

* {
  padding: 0;
  margin: 0;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  align-items: flex-start;
  justify-content: center;

  min-height: 100vh;

  .container {
    width: 250px;
    height: 400px;
    margin: 50px auto;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    position: relative;

    nav {
      display: flex;
      justify-content: flex-end;
      align-content: center;

      i {
        position: absolute;
        right: 0;
        top: -5px;
        color: #111;
        transition: 0.3s all;
        font-size: 1.5rem;
      }
      .sun-icon {
        color: rgb(232, 232, 58);
      }
      .dark-icon {
        color: #333;
      }
    }
    article {
      background-color: #fff;
      padding: 15px;
      color: #111;
      img {
        width: 100%;
      }

      p {
        font-size: 1rem;

        &::first-letter {
          font-size: 2rem;
          font-weight: 600;
        }
      }
    }
  }
  &.theme-dark {
    background-color: #333;
    color: #efefef;
    article {
      background-color: #222;
      border-radius: 5px;
      border: 1px solid #555;
      color: #efefef;
    }
  }
  .fade-enter,
  .fade-leave {
    opacity: 0;
  }

  .fade-enter-active,
  .fade-leave-active {
    opacity: 1;
    transition: 0.3s all opacity;
  }
}
</style>
