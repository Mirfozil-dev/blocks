<template>
  <div id="app">
    <div :class="`circle_item__${item}`" v-for="item in 4" :key="item">
      <circle-item :id="item" />
    </div>
    <div class="board__wrapper">
      <board v-for="(item, index) in boards" :key="index" :board="item" />
    </div>
  </div>
</template>

<script>

import CircleItem from './components/CircleItem.vue';
import Board from './components/Board.vue';

export default {
  name: 'App',
  data() {
    return {
      boards: [
        {
          title: 'A',
          color: 'yellow',
          canHold: [1, 2],
        },
        {
          title: 'B',
          color: 'blue',
          canHold: [1, 2],
        },
        {
          title: 'C',
          color: 'green',
          canHold: [3, 4],
        },
        {
          title: 'D',
          color: 'purple',
          canHold: [3, 4],
        },
      ],
    };
  },
  components: {
    CircleItem,
    Board,
  },
};
</script>

<style>

.board__wrapper {
  width: 300px;
  height: 300px;
  display: flex;
  flex-wrap: wrap;
  margin: 0 auto;
  padding-top: 10%;
  z-index: 2;
}

.circle_item__1, .circle_item__2, .circle_item__3, .circle_item__4 {
  position: absolute;
}

.circle_item__1, .circle_item__2 {
  top: 10px;
}

.circle_item__3, .circle_item__4 {
  bottom: 10px;
}

.circle_item__1, .circle_item__3 {
  left: 10px;
}

.circle_item__2, .circle_item__4 {
  right: 10px;
}
</style>
