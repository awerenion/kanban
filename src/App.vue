<template>
  <div class="container">
    <v-board
      v-for="board in $options.BOARDS"
      :id="board.id"
      :key="board.id"
    >
      <template #boardName>
        {{ board.name }}
      </template>
      <template #item>
        <v-item
          v-for="item in board.cards"
          :id="item.id"
          :key="item.id"
          :draggable="item.draggable"
        >
          <template #itemName>
            {{ item.name }}
          </template>
        </v-item>
      </template>
    </v-board>
  </div>
</template>

<script>
import BOARDS from '@/constants/boards'
import VBoard from '@/components/Board'
import VItem from '@/components/Item'

export default {
  name: 'App',
  components: {
    VBoard,
    VItem
  },
  BOARDS
}
</script>

<style lang="scss" scoped>
.container {
  height: 100%;
  width: 100%;
  display: flex;
  align-items: center;
}
</style>
