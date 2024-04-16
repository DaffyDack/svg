<template>
  <div class="b-map-svg">
    <div class="wrapper">
      <svg xmlns="http://www.w3.org/2000/svg" xml:space="preserve" width="514px" height="516px" version="1.1"
        style="shape-rendering:geometricPrecision; text-rendering:geometricPrecision; image-rendering:optimizeQuality; fill-rule:evenodd; clip-rule:evenodd"
        viewBox="0 0 514 516" xmlns:xlink="http://www.w3.org/1999/xlink">
        <g v-for="(item, index) in pie" :key="index">
          <polygon :class=item.id @mouseover="onMouseover" @mouseout="onMouseout" :points=item.points />
        </g>
      </svg>
      <ul class="list">
        <li v-for="(item, index) in items" :key="index" :class="{ active: change == item.id }" :id=item.id>{{ item.title }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script >
export default {
  name: 'App',
  data() {
    return {
      items: [
        { id: 'fil1', title: 'Розовый' },
        { id: 'fil2', title: 'Зеленый' },
        { id: 'fil3', title: 'Серый' }
      ],
      pie: [
        { id: 'fil1', points: '208, 508, 256, 257, 513, 258, 512, 272, 511, 289, 509, 307, 505, 326, 498, 349, 489, 368, 480, 388, 467, 409, 455, 424, 438, 440, 421, 455, 403, 470, 380, 483, 352, 495, 327, 504, 302, 510, 279, 512, 251, 512, 229, 511' },
        { id: 'fil2', points: '258, 259, 149, 23, 129, 33, 116, 41, 99, 54, 83, 68, 68, 83, 53, 102, 39, 123, 28, 142, 18, 165, 12, 180, 6, 203, 3, 227, 1, 252, 2, 273, 4, 295, 9, 321, 16, 345, 24, 365, 34, 385, 44, 403, 57, 420, 71, 436, 91, 453, 108, 466, 129, 479, 148, 489, 168, 497, 185, 503, 199, 506, 208, 508' },
        { id: 'fil3', points: '256, 258, 148, 24, 168, 16, 185, 11, 203, 7, 222, 4, 239, 2, 261, 1, 285, 3, 312, 7, 339, 15, 360, 24, 385, 36, 406, 50, 421, 63, 441, 80, 460, 100, 474, 122, 486, 144, 496, 166, 504, 191, 510, 216, 512, 239, 513, 258' }
      ],
      change: ''
    }
  },
  methods: {
    onMouseover(e) {
      this.change = e.target.className.baseVal
    },
    onMouseout() {
      this.change = ''
    }
  }

}
</script>
<style scoped lang="scss">
$colors: #FF69B4, #97BB31, #4d50d9;

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.wrapper {
  display: flex;
}

ul {
  list-style-type: none;
}

.list {
  padding: 50px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.b-map-svg {
  position: relative;
  width: 1000px;
}
g {
  cursor: pointer
}

@for $i from 1 through length($colors) {
  #fil#{$i} {
    width: 280px;
    max-width: 100%;
    height: auto;
    padding: 20px 20px 20px 50px;
    position: relative;
    color: rgb(132, 131, 131);
    &::after {
      content: '';
      width: 20px;
      height: 20px;
      background: nth($colors, $i);
      position: absolute;
      left: 0;
      top: 50%;
      transform: translateY(-50%);
    }
    &.active {
      text-decoration: underline red;
      color: #000;
    }
  }

  .fil#{$i} {
    fill: nth($colors, $i);

    &:hover {
      filter: grayscale(100%);
      transition: filter 1s linear;
    }
  }
}
</style>

