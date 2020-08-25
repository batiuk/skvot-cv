<template>
  <div id="cv">
    <div class="navigation-block">
      <input v-model="isMenuOpened" type="checkbox">
      <div @click="isMenuOpened=!isMenuOpened" class="menu">
        <span class="hamburger"></span>
      </div>
      <transition name="fade">
        <nav v-show="isMenuOpened">
          <json-nav
            v-show="isMenuOpened"
            :value="jsonObj"
            :expand-depth="1">

          </json-nav>
        </nav>
      </transition>
    </div>
    <main>
      <div class="bg">
        <div class="block block-1"></div>
        <div class="block block-2"></div>
        <div class="block block-3"></div>
        <div class="block block-4"></div>
        <div class="block block-5"></div>
        <div class="block block-6"></div>
      </div>
      <div class="cs-block">
        <h1 class="fullname">Volodymyr Batiuk</h1>
        <h2 class="position">Front-End Developer</h2>
        <div class="contacts">
          <a href="tel:+38(095)7485107" class="phone">+38 (095) 74 85 107</a>
          <a href="mailto:v@bati.uk" class="email">v@bati.uk</a>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import jsonNav from './components/json-nav/index.vue';
import jsonObj from './common/json/cs.json';

export default {
  name: 'cv',
  components: { jsonNav },
  data() {
    return {
      jsonObj,
      isMenuOpened: false,
    };
  },
};
</script>
<style lang="scss" src="./common/styles/imports.scss">
</style>
<style lang="scss" scoped>
  #cv {
    z-index: 10;
    background-color: #F0F0F0;
    width: 100vw;
    height: 100vh;

    .navigation-block {
      position: fixed;
      z-index: 10;

      .hamburger {
        position: absolute;
        top: 135px;
        right: 50px;
        width: 30px;
        height: 2px;
        background: #F0F0F0;
        display: block;
        -webkit-transform-origin: center;
        transform-origin: center;
        -webkit-transition: .5s ease-in-out;
        transition: .5s ease-in-out;
      }

      .hamburger:after, .hamburger:before {
        -webkit-transition: .5s ease-in-out;
        transition: .5s ease-in-out;
        content: "";
        position: absolute;
        display: block;
        width: 100%;
        height: 100%;
        background: #F0F0F0;
      }

      .hamburger:before {
        top: -10px;
      }

      .hamburger:after {
        bottom: -10px;
      }

      input {
        display: none;
      }

      input:checked + .menu {
        box-shadow: 0 0 0 100vw #282C34, 0 0 0 100vh #282C34;
        border-radius: 0;
        transition: .6s ease-in-out;
      }

      input:checked + .menu .hamburger {
        -webkit-transform: rotate(45deg);
        transform: rotate(45deg);
      }

      input:checked + .menu .hamburger:after {
        -webkit-transform: rotate(90deg);
        transform: rotate(90deg);
        bottom: 0;
      }

      input:checked + .menu .hamburger:before {
        -webkit-transform: rotate(90deg);
        transform: rotate(90deg);
        top: 0;
      }

      input:checked + .menu {
        opacity: 1;
      }

      .menu {
        position: absolute;
        left: -100px;
        top: -100px;
        width: 200px;
        height: 200px;
        background: #282C34;
        border-radius: 50% 50% 50% 50%;
        -webkit-transition: .6s ease-in-out;
        transition: .6s ease-in-out;
        box-shadow: 0 0 0 0 #282C34, 0 0 0 0 #282C34;
        cursor: pointer;
      }

      .fade-enter-active, .fade-leave-active {
        opacity: 1;
        transition: opacity .4s;
        transition-delay: .2s;
      }

      .fade-enter, .fade-leave-to /* .fade-leave-active до версии 2.1.8 */
      {
        opacity: 0;
        transition: opacity .4s;
      }

      nav {
        width: 100vw;
        height: 100vh;
        padding-left: 100px;
        padding-top: 100px;

        .jv-container {
        }
      }

    }

    main {
      .bg {
        display: flex;
        width: 100vw;

        .block {
          width: calc(100vw / 6);
          min-width: 200px;
          height: 100vh;

          &-1 {
            background: #EF596F;
          }

          &-2 {
            background: #E5C07B;
          }

          &-3 {
            background: #89CA78;
          }

          &-4 {
            background: #61AFEF;
          }

          &-5 {
            background: #2BBAC5;
          }

          &-6 {
            background: #D55FDE;
          }
        }
      }

      .cs-block {
        color: #282C34;
        font-family: Graphik, sans-serif;
        position: absolute;
        top: 0;
        left: 0;
        width: 100vw;
        min-width: 1200px;
        height: 100vh;
        display: flex;
        flex-direction: column;
        align-items: center;

        .fullname {
                    margin-top: 35vh;
          font-weight: bold;
          font-size: 96px;

        }

        .position {
          margin-top: 20px;
          font-weight: 500;
          font-size: 48px;

        }

        .contacts {
          display: flex;
          margin-top: 30vh;
          flex-direction: column;
          align-items: center;

          a {
            text-decoration: none;
            color: #282C34;
            font-size: 48px;
                                    font-weight: 500;
            transition: .5s;

            &:hover {
              color: #EF596F;
                        font-weight: 500;
              transition: .5s;
            }

            .phone {

            }

            .email {
              margin-top: 20px;

            }
          }
        }
      }
    }
  }
</style>
