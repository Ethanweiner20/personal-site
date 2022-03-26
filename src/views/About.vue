<template>
  <div class="page">
    <Header title="ABOUT ME" />
    <div class="row p-3 pt-0 pt-sm-3 mt-sm-5">
      <div class="col-lg-3 col-sm-4 col-12 p-sm-3 p-5" id="profile">
        <img
          class=""
          src="../assets/images/Portrait_Square.jpg"
          alt="Profile Pic"
        />
        <div class="socials mt-3">
          <div class="social-button d-inline">
            <div
              class="g-ytsubscribe social-button d-inline"
              data-channelid="UCsQWJH88fdSZDgZpAHFb11w"
              data-layout="default"
              data-count="hidden"
            ></div>
          </div>

          <div class="social-button d-inline">
            <a
              class="github-button social-button"
              href="https://github.com/EthanWeiner20"
              data-size=""
              aria-label="Follow @EthanWeiner20 on GitHub"
              >@EthanWeiner20</a
            >
          </div>

          <div class="social-button d-inline">
            <a
              class="github-button social-button"
              href="https://github.com/EthanWeiner20"
              data-size=""
              aria-label="Follow @EthanWeiner20 on GitHub"
              >@EthanWeiner20</a
            >
          </div>
        </div>
      </div>
      <div
        class="
          col-lg-9 col-12 col-sm-8
          p-sm-2 p-sm-5 p-3
          py-0
          text-start
          mb-4
          mr-5
        "
      >
        <p class="mr-5" id="about-introduction">
          Hi, I'm Ethan. I'm an aspiring software engineer. Click on the tabs to learn
          more about me.
        </p>
      </div>
    </div>
    <div class="p-3 p-lg-5 pt-0 pt-sm-3 mx-lg-4 mx-0">
      <ul
        class="nav nav-tabs nav-justified flex-sm-row flex-column"
        id="about-tabs"
        role="tablist"
      >
        <li class="nav-item active" role="presentation">
          <div class="cornered" data-bs-target="#mission-tab"></div>
          <button
            class="nav-link active text-white"
            id="mission-tab"
            data-bs-toggle="tab"
            data-bs-target="#mission"
            type="button"
            role="tab"
            aria-controls="mission"
            aria-selected="true"
          >
            MY MISSIONS
          </button>
        </li>
        <li class="nav-item" role="presentation">
          <div
            class="cornered"
            data-bs-target="#education-experience-tab"
          ></div>
          <button
            class="nav-link text-white"
            id="education-experience-tab"
            data-bs-toggle="tab"
            data-bs-target="#education-experience"
            type="button"
            role="tab"
            aria-controls="education-experience"
            aria-selected="true"
          >
            EDUCATION/EXPERIENCE
          </button>
        </li>
        <li class="nav-item" role="presentation">
          <div class="cornered" data-bs-target="#outside-software-tab"></div>
          <button
            class="nav-link text-white"
            id="outside-software-tab"
            data-bs-toggle="tab"
            data-bs-target="#outside-software"
            type="button"
            role="tab"
            aria-controls="outside-software"
            aria-selected="true"
          >
            OUTSIDE SOFTWARE
          </button>
        </li>
      </ul>
      <div class="tab-content mb-5 text-start p-sm-5 p-3" id="about-content">
        <div
          class="tab-pane fade show active"
          id="mission"
          role="tabpanel"
          aria-labelledby="mission-tab"
        >
          <p>
            Throughout my journey, I have constructed a set of "missions" through which I seek to make an impact as a developer:
            <ul class="mt-3">
              <Mission name="automation">
                <template v-slot:mission-name>
                  Automate and enhance systems and workflows
                </template>
                <template v-slot:mission-description>
                    I am obsessed with automating tedious or repetitive processes, both in and outside of software. I strongly believe that individuals and groups can be
                    more productive, meaningful, and fulfilled by establishing well-designed systems, routines, and automated processes.
                    For example, I developed an application to simplify employer-employee interaction at small companies. I created a portal to automate aspects of the scholarship application process.
                    As such, I seek to build applications and plugins that automate the more time-consuming, but less fulfilling tasks and procedures. Likewise, I hope
                    to assist in automating the development process itself, streamlining the development workflow for businesses.
                </template>
              </Mission>

              <Mission name="design">
                <template v-slot:mission-name>
                  Produce well-designed code and well-designed software
                </template>

                <template v-slot:mission-description>
                    Ever since I was exposed to the concept of proper program design, I made it a personal mission to
                    design code as best as I reasonably could. I seek to not only finish programs, but design them well,
                    such that they are maintanable and scalable. I document and test my code thoroughly, 
                    adhere to object-oriented programming principles, and ensure my code is as readable as possible. I recognize
                    that keeping code properly designed and organized facilitates the clarity that is crucial to
                    expand and update software.
                </template>
              </Mission>

            </ul>
          </p>
        </div>
        <div
          class="tab-pane fade"
          id="education-experience"
          role="tabpanel"
          aria-labelledby="education-experience-tab"
        >
          <p>
            My interest in software development began as early as software, but I didn't get serious about the practice
            until pursuing a degree in Computer Science. During my brief period at college, I learned quite a lot about 
            programming fundamentals, discrete mathematics, and formal reasoning. However, I found the learning
            environment at college to be restricting, and I ended up deciding to pursue a journey to self-teach
            the fundamentals of software engineering, with the help of a rigorous mastery-based program known as Launch School.
            Since leaving, I have been honing in on my skills as a developer while working part-time. I completed
            Harvard's CS50x course, and I am diving into the core curriculum at Launch School.
            I have developed a variety of <router-link :to="{name: 'Projects'}">projects</router-link>along the way,
            gaining some experience as a freelancer for a small landscape design company and former high school.
          </p>
        </div>
        <div
          class="tab-pane fade"
          id="outside-software"
          role="tabpanel"
          aria-labelledby="outside-software-tab"
        >
          <p>
            Outside of the realm of software engineering, I am a competitive long-distance runner, <a href="https://www.youtube.com/channel/UCsQWJH88fdSZDgZpAHFb11w" target="_blank">small Youtuber</a>, and landscaper.
            I am passionate about mental health, psychiatry, and philosophy.
            I work for a small landscape design and maintenance company. Check out some of my designs!
            <ul class="mt-3">
              <li>
                <a href="https://youtu.be/DRk6x5dLGaI" target="_blank">https://youtu.be/DRk6x5dLGaI</a>
              </li>
              <li>
                <a href="https://youtu.be/VhhBNszLIjM" target="_blank">https://youtu.be/VhhBNszLIjM</a>
              </li>
            </ul>
          </p>


        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { onMounted } from '@vue/runtime-core'
import { clearCanvas } from '../assets/helpers'
import Header from '../components/Header'
import Mission from '../components/Mission'

export default {
  name: 'About',
  components: {
    Header,
    Mission
  },
  mounted() {
    // Initialize the buttons
    let youtubeScript = document.createElement('script')
    youtubeScript.setAttribute('src', 'https://apis.google.com/js/platform.js')
    document.head.appendChild(youtubeScript)

    let githubScript = document.createElement('script')
    githubScript.setAttribute('src', 'https://buttons.github.io/buttons.js')
    githubScript.setAttribute('async', 'true')
    githubScript.setAttribute('defer', 'true')
    document.head.appendChild(githubScript)

    document.querySelectorAll('.cornered').forEach((container) => {
      container.addEventListener('click', (e) => {
        const tab_id = container.getAttribute('data-bs-target')
        var el = document.querySelector(tab_id)
        var tab = new bootstrap.Tab(el)
        tab.show()
      })
    })
  }
}
</script>

<style lang="scss">
@import '@/assets/styles.scss';

  #about-introduction {
    @media (max-width: 900px) {
      font-size: 30px;
    }
    font-size: 40px;
  }

#about-content {
  background-color: lighten($main-dark, 5);
  height: fit-content;
}
.nav {
  border: none;
  border-bottom: 1px solid $main-grey;
  background-color: lighten($main-dark, 5);

  font-size: 25px;
  @media (max-width: 850px) {
    font-size: 17px;
  }
  @media (max-width: 575px) {
    font-size: 22px;
  }
  .nav-item,
  .nav-link {
    height: 70px;
    cursor: pointer;
    &:hover {
      border: none;
      background-color: $main-grey;
      border-bottom: 1px solid white;
    }
  }
  .nav-link.active {
    background: $main-grey;
    border-bottom: 3px solid white;
  }
  .cornered {
    width: 100%;
    height: 0px;
    border-bottom: 70px solid transparent;
    border-right: 30px solid $main-dark;
    border-left: 30px solid $main-dark;
    z-index: 100 !important;
    position: relative;
    @media (max-width: 575px) {
      visibility: hidden;
    }
  }
  li {
  }
  button,
  a {
    margin-top: -70px;
    border: none;
    position: relative;
    z-index: 1;
  }
}
#profile {
  position: relative;
  img {
    border-radius: 1500px;
    border: 3px solid white;
    width: 250px;
    @media (max-width: 1000px) {
      width: 200px;
    }

    @media (max-width: 850px) {
      width: 175px;
    }

    @media (max-width: 700px) {
      width: 125px;
    }

    @media (max-width: 575px) {
      width: 225px;
    }
  }
  #socials {
    width: 300px;
    @media (max-width: 600px) {
      width: 150px;
    }
  }
}

.social-button {
  margin: 0 5px !important;
}

.tab-content {
  p {
    font-size: 22px;
  }

}
</style>
