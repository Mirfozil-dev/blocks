<template>
  <div
      class="board"
      @dragover.prevent
      @dragenter.prevent
      @drop.prevent="drop"
  >
    <svg width="100%" height="100%">
      <g>
        <rect width="100%" height="100%" :fill="board.color"></rect>
        <text x="45%" y="55%" fill="black">
          {{ board.title }}
        </text>
        <foreignObject x="30%" y="30%" height="40%" width="40%">
        </foreignObject>
      </g>
    </svg>
  </div>
</template>

<script>
export default {
  name: 'Board',
  props: {
    board: Object,
  },
  methods: {
    drop(e) {
      const boardSvg = e.target.closest('.board>svg').children[0].children[2];
      const card_id = e.dataTransfer.getData('card_id');
      this.board.canHold.map(item => {
        if (boardSvg.children.length < 1 && item === parseInt(card_id)) {
          const card = document.getElementById(card_id);
          boardSvg.appendChild(card);
        }
      });
    },
  },
};
</script>

<style scoped>
.board {
  width: 49.3%;
  height: 49.3%;
  font-size: 30px;
}
</style>