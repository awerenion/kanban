<template>
  <div
    :id="id"
    class="item"
    :draggable="draggable"
    @dragstart="dragStart"
    @dragover.stop
  >
    <slot name="itemName" />
  </div>
</template>

<script>
export default {
  props: {
    id: {
      type: String,
      required: true
    },
    draggable: {
      type: Boolean,
      required: true
    }

  },
  methods: {
    dragStart: el => {
      const target = el.target

      el.dataTransfer.setData('item_id', target.id)
    }
  }
}
</script>

<style lang="scss" scoped>
.item {
  padding: 10px;
  border-radius: 10px;
  margin-bottom: 10px;
  border: 1px solid #000;
}

.item:last-child {
  margin-bottom: 0;
}
</style>
