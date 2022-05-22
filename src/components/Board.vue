<template>
  <div class="board-wrapper">
    <div class="board-title">
      <slot name="boardName" />
    </div>
    <div
      :id="id"
      class="board"
      @dragover.prevent
      @drop.prevent="drop"
    >
      <slot name="item" />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    id: {
      type: String,
      required: true
    }
  },
  methods: {
    drop: el => {
      const itemId = el.dataTransfer.getData('item_id')

      const item = document.getElementById(itemId)

      item.style.display = 'block'

      el.target.appendChild(item)
    }
  }
}
</script>

<style scoped>
.board-wrapper {
  height: 80%;
  width: 150px;
  margin-left: 50px;
  display: flex;
  flex-direction: column;
}
.board-wrapper:first-child {
  margin-left: 0;
}

.board-title {
  margin-bottom: 5px;
  text-align: center;
}

.board {
  height: 100%;
  width: 100%;
  border-radius: 20px;
  padding: 10px;
  box-shadow: 0 20px 25px -5px rgba(0,0,0,.1),0 10px 10px -5px rgba(0,0,0,.04);
  background: #fff;
}

</style>
