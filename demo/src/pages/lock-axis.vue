<template>
  <div class="simple-page">
    <Container @drop="onDrop" lock-axis="y">
      <SmoothDraggable v-for="item in items" :key="item.id">
        <div class="draggable-item">
          {{item.data}}
        </div>
      </SmoothDraggable>
    </Container>
  </div>
</template>

<script>
import { Container, SmoothDraggable } from 'vue-smooth-dnd'
import { applyDrag, generateItems } from '../utils/helpers'

export default {
  name: 'LockAxis',

  components: {Container, SmoothDraggable},

  data () {
    return {
      items: generateItems(50, i => ({id: i, data: 'Draggable ' + i}))
    }
  },

  methods: {
    onDrop (dropResult) {
      this.items = applyDrag(this.items, dropResult)
    }
  }
}
</script>
