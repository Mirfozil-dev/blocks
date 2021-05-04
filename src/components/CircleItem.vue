<template>
  <div
      :id="id"
      draggable="true"
      class="circle_item__body"
      @dragstart="dragStart"
      @dragover.prevent
  >
    <svg
        width="100%"
        height="100%"
    >
      <circle r="25" cx="25" cy="25" fill="teal" />
      <text x="40%" y="60%" fill="black">
        {{ id }}
      </text>
    </svg>
  </div>
</template>

<script>
export default {
  name: 'CircleItem',
  props: ['id'],
  methods: {
    dragStart: e => {
      const target = e.target;
      e.dataTransfer.setData('card_id', target.id);
    },
  },
};
</script>

<style scoped>
.circle_item__body {
  width: 50px;
  height: 50px;
  font-size: 25px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: grab;
}

.circle_item__body:active {
  cursor: grabbing;
}
</style>