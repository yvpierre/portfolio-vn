<template>
  <Cursor />
  <main>
    <h1>
      I'm&nbsp;<em>Pierre Yvenou</em><br/>a 20 years old <br/>fond of
      <div class="scrollerDingo">
        <div class='wrapper'>
          <div class="item--1 item--anim anim">True detective</div>
          <div class="item--2 item--anim anim">Museums</div>
        </div>
      </div>
    </h1>
    <svg width="200" height="200" class="rotating-text">
      <path id="curve" fill="transparent"
            d="
        M 50, 100
        a 50,50 0 1,1 100,0
        a 50,50 0 1,1 -100,0
         " />
      <text width="1000px" font-size="40px" class="svg-text" >
        <textPath xlink:href="#curve" >
          Life is gooooood •
        </textPath>
      </text>
    </svg>

  </main>
</template>

<script>
import Cursor from "@/components/Cursor.vue";
export default {
  components: {Cursor},
  data() {
    return {
      likes: [
          "Frontend development", "True detective", "Museums", "House music", "Cycling", "Cooking", "Traveling", "Reading"
      ]
    }
    },
  methods: {
    getRandomInt : function (max) {
      return Math.floor(Math.random() * max);
    },
    changeText() {
      const wrapper = document.querySelector('.wrapper');
      const item1 = document.querySelector('.item--1');
      const item2 = document.querySelector('.item--2');
      const text1 = item1.textContent;
      const text2 = this.likes[this.getRandomInt(this.likes.length)];
      if (text2 === text1) return; // Avoid repeating the same text
      item1.textContent = text2;
      item2.textContent = text1;
      wrapper.classList.add('animate');
      console.log("added")
      setTimeout(() => {
        console.log("removed")
        wrapper.classList.remove('animate');
      }, 1500);
    },

  },
  mounted() {
      setInterval(this.changeText, 2500);
  }
}

</script>

<style lang="scss" scoped>
@import "@/styles/main.scss";

h1 {
  margin: 100px 0 0 50px;
  font-size: 48px;
  font-weight: 200;
  width: 500px;
  border: 1px solid red;
  position: relative;

  em {
    color: $purple;
    font-style: normal;
    font-weight: 400;
  }

  .scrollerDingo {
    height: 50px;
    line-height: 50px;
    position: relative;
  }

  .scrollerDingo  > div {
    display: block;
    position: absolute;
    line-height: 50px;
    animation-fill-mode: forwards;
    color: $purple;
    top: 0;
    left: 0;
    height: 50px;
    pointer-events: none;
    font-weight: 400;
  }

  .item--anim {
    position: absolute;
    opacity: 1;
    pointer-events: none;
    min-width: 500px !important;
  }

  .item--2 {
    top: 50px;
  }

  .wrapper.animate .item--1 {
    animation: slideUp 1s forwards;
  }

  .wrapper.animate .item--2 {
    animation: slideDown 1s forwards;
  }
}



@keyframes slideUp {
  0% {
    top: 0;
  }
  100% {
    top: -50px;
  }
}

@keyframes slideDown {
  0% {
    top: 50px;
  }
  100% {
    top: 0;
  }
}


@keyframes rotate {
  100% {
    transform: rotate(-1turn);
  }
}

.rotating-text {
  position: absolute;
  fill: $navy !important;
  right: 100px;
  top: 200px;
  font-family: 'Times New Roman', serif;
  animation: rotate 5s linear infinite;
  transform-origin: 50% 50%;
  transition: 1s fill
}

.rotating-text:hover {
  animation-play-state: paused;
}


</style>
