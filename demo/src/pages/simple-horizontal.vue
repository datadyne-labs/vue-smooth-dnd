<template>
  <div style="margin: 50px; overflow-x: auto">
    <Container @drop="onDrop" orientation="horizontal" behaviour="contain">
      <SmoothDraggable v-for="item in items" :key="item.id">
        <div class="draggable-item-horizontal">
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
  name: 'SimpleHorizontal',

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
