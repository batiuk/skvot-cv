<template>
  <div id="portfolio">
    <main class="portfolio-main" v-show="!isMenu">
      <section id="portfolioBlock" class="section-block">
        <span id="portPart">PORT</span>
        <span id="folioPart">FOLIO</span>
      </section>
      <section id="aboutBlock" class="section-block">
        <div class="header">About <br/>Me</div>
        <div class="figure circle"></div>
        <div class="content">
          <span class="fullname">Batiuk <br/>Volodymyr</span>
          <div class="divider"></div>
          <span class="position">Front-End Developer</span>
          <div class="divider"></div>
          <span class="description">Experienced Frontend Developer with a demonstrated history of
            working in the information technology and services industry. Skilled in Vue.js,
            JavaScript, WordPress, and Web Services. Strong engineering professional with
            a Bachelor's degree focused in Computer Software Engineering from Zhytomyr
            State Technological University.
          </span>
          <div class="divider"></div>
        </div>
      </section>
      <section class="section-block" id="experienceBlock">
        <div class="header">exper<br/>ience</div>
        <div class="figure square"></div>
        <div class="content">
          <div class="work">
            <div class="divider"></div>
            <div class="row" @click="work1Show = !work1Show">
              <span class="position">Junior Front-End Developer</span>
              <img class="arrow arrow-for-click" :class="{'opened':work1Show}"
                   :src="arrow" alt="Arrow Image"/>
            </div>
            <div v-show="work1Show" class="work-info">
              <div class="divider"></div>
              <div class="row">
                <span class="company">Company</span>
                <span class="company">Viseven</span>
              </div>
              <div class="divider"></div>
              <div class="row">
                <span class="dates">Dates</span>
                <span class="dates">Aug 2019 - Present</span>
              </div>
              <div class="divider"></div>
              <div class="row">
                <span class="city">City</span>
                <span class="city">Zhytomyr, Ukraine</span>
              </div>
              <div class="divider"></div>
            </div>
            <div v-show="!work1Show" class="divider"></div>
          </div>
        </div>
      </section>
      <section class="section-block" id="educationBlock">
        <div class="header">educ<br/>ation</div>
        <div class="figure triangle"></div>
        <div class="content">
          <div class="education">
            <div class="divider"></div>
            <div class="row" @click="education1Show = !education1Show">
              <span class="degree">Bachelor's degree</span>
              <img class="arrow arrow-for-click" :class="{'opened':education1Show}"
                   :src="arrow" alt="Arrow Image"/>
            </div>
            <div v-show="education1Show" class="education-info">
              <div class="divider"></div>
              <div class="row">
                <span class="university">University</span>
                <A href="https://ztu.edu.ua/" class="university">ZSTU</A>
              </div>
              <div class="divider"></div>
              <div class="row">
                <span class="dates">Dates</span>
                <span class="dates">Sep 2016 - Jun 2020</span>
              </div>
              <div class="divider"></div>
              <div class="row">
                <span class="city">City</span>
                <span class="city">Zhytomyr, Ukraine</span>
              </div>
              <div class="divider"></div>
            </div>
            <div v-show="!education1Show" class="divider"></div>
          </div>
        </div>
      </section>
      <section class="section-block" id="skillsBlock">
        <div class="header">skills</div>
        <div class="figure triangle-down"></div>
        <div class="content">
          <span class="title">General</span>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">JavaScript</span>
            <span class="level">Good</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">HTML5</span>
            <span class="level">Perfect</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">CSS3</span>
            <span class="level">Perfect</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">SASS/SCSS</span>
            <span class="level">Good</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">Vue.js</span>
            <span class="level">Good</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">Node.js</span>
            <span class="level">Good</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">Git</span>
            <span class="level">Good</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">Express.js</span>
            <span class="level">Normal</span>
          </div>
          <div class="divider"></div>
        </div>
        <div class="content-rotate">
          <span class="title">Languages</span>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">Ukrainian</span>
            <span class="level">Native</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">Russian</span>
            <span class="level">Native</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">English</span>
            <span class="level">Intermediate</span>
          </div>
          <div class="divider"></div>
        </div>
        <div class="content">
          <span class="title">CMS</span>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">WordPress</span>
            <span class="level">Good</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">Strapi.js</span>
            <span class="level">Good</span>
          </div>
          <div class="divider"></div>
        </div>
        <div class="content-rotate">
          <span class="title">Amazon Web Services</span>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">AWS Lambda</span>
            <span class="level">Good</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">AWS RDS</span>
            <span class="level">Normal</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">AWS Amplify</span>
            <span class="level">Perfect</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <span class="skill">AWS EC2</span>
            <span class="level">Normal</span>
          </div>
          <div class="divider"></div>
        </div>
      </section>
      <section class="section-block" id="projectsBlock">
        <div class="header-wrapper">
        <div class="header" :class="{'fixed':isProjectBlock}">proj<br/>ects</div>
        </div>
        <div class="figure square"></div>
        <div class="content">
          <div class="divider"></div>
          <div class="row">
            <a class="project-link">Project 7
              <img class="project-link-arrow" :src="linkArrow" alt="Arrow link"/>
            </a>
            <span class="project-date">Apr  2020</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <a class="project-link">Project 6
              <img class="project-link-arrow" :src="linkArrow" alt="Arrow link"/>
            </a>
            <span class="project-date">Mar  2020</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <a class="project-link">Project 5
              <img class="project-link-arrow" :src="linkArrow" alt="Arrow link"/>
            </a>
            <span class="project-date">Feb  2020</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <a class="project-link">Project 4
              <img class="project-link-arrow" :src="linkArrow" alt="Arrow link"/>
            </a>
            <span class="project-date">Jan  2020</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <a class="project-link">Project 3
              <img class="project-link-arrow" :src="linkArrow" alt="Arrow link"/>
            </a>
            <span class="project-date">Dec  2019</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <a class="project-link">Project 2
              <img class="project-link-arrow" :src="linkArrow" alt="Arrow link"/>
            </a>
            <span class="project-date">Nov  2019</span>
          </div>
          <div class="divider"></div>
          <div class="row">
            <a class="project-link">Project 1
              <img class="project-link-arrow" :src="linkArrow" alt="Arrow link"/>
            </a>
            <span class="project-date">Sep  2019</span>
          </div>
          <div class="divider"></div>
        </div>
      </section>
      <section class="section-block" id="contactsBlock">
        <div class="header-wrapper">
          <div class="header" :class="{'fixed':isContactBlock,}">Cont<br/>acts</div>
        </div>
        <div class="figure circle"></div>
        <div class="content">
          <div class="divider"></div>
          <span class="address">
            60 Kyiv str., Korostushiv,<br/>
            Zhytomyrska oblast, Ukraine<br/>
            +380 95 74 85 107<br/></span>
          <div class="divider"></div>
          <div class="row">
            <span class="email">Email</span>
            <span class="email">v@bati.uk</span>
          </div>
          <div class="divider b-m-60"></div>
          <div class="row">
            <a class="link" href="https://www.linkedin.com/in/v-batiuk/">
              LinkedIn
            </a>
            <a class="arrow-link" href="https://www.linkedin.com/in/v-batiuk/">
              <img class="arrow" :src="linkArrow" alt="Arrow link"/>
            </a></div>
          <div class="divider big"></div>
          <div class="row">
            <a class="link" href="https://www.instagram.com/bati.uk/">
              Instagram
            </a>
            <a class="arrow-link" href="https://www.instagram.com/bati.uk/">
              <img class="arrow" :src="linkArrow" alt="Arrow link"/>
            </a>
          </div>
          <div class="divider big"></div>
          <div class="row">
            <a class="link">
              Telegram
            </a>
            <a class="arrow-link" href="#">
              <img class="arrow" :src="linkArrow" alt="Arrow link"/>
            </a>
          </div>
          <div class="divider big"></div>
          <span class="copyright">©2020, v.bati.uk</span>
        </div>
      </section>
    </main>
    <nav v-show="isMenu" class="menu-main">
      <json-nav
        :value="jsonObj"
        :expand-depth="1">

      </json-nav>
    </nav>
    <button class="menu-button" @click="isMenu = !isMenu">{{!isMenu?'JSON':'Design'}}</button>
  </div>
</template>

<script>
import linkArrow from './common/images/arrow-top-r.svg';
import arrow from './common/images/arrow-top.svg';
import jsonNav from './components/json-nav/index.vue';
import jsonObj from './common/json/cs.json';

export default {
  name: 'portfolio',
  components: { jsonNav },
  data() {
    return {
      linkArrow,
      arrow,
      jsonObj,
      isMenu: false,
      work1Show: true,
      education1Show: true,
      isContactBlock: false,
      isProjectBlock: false,
    };
  },
  mounted() {
    document.addEventListener('scroll', () => {
      const contactBlock = document.getElementById('contactsBlock');
      this.isContactBlock = contactBlock.offsetTop <= window.pageYOffset;
      const projectBlock = document.getElementById('projectsBlock');
      this.isProjectBlock = projectBlock.offsetTop <= window.pageYOffset;
    });
  },
};
</script>
<style lang="scss" src="./common/styles/imports.scss">
</style>
<style lang="scss" scoped>
  @import "common/styles/variables";
  #portfolio {
    z-index: 10;
    background-color: #F0F0F0;
    width: 100vw;
    height: 100vh;

    nav.menu-main {
      width: 100%;
      padding: 20px;
      min-height: 100vh;
      background: $blackColor;
    }

    .menu-button {
      position: fixed;
      bottom: 20px;
      right: 20px;
    }
  }
</style>
