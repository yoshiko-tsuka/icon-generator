<template>
  <div class="row">
    <div class="col-6">
      <p><img @mousedown="mDown" @mousemove="mMove" @mouseup="mUp" class="drag-and-drop" src="/sea.png"></p>
    </div>
    <div class="col-6">
    </div>
  </div>
</template>

<script>
let id = 1;
export default {
  name: 'simple',
  display: 'Simple',
  layout: 'menu',
  data () {
    return {
      x: 0,
      y: 0,
      is_mousedown: false
    }
  },
  methods: {
    mDown () {
      this.x = event.pageX - this.$el.offsetLeft
      this.y = event.pageY - this.$el.offsetTop
      this.is_mousedown = true
      console.log("DOWN X:" + event.pageX + " Y:" + event.pageY + " OffsetLeft:" + this.$el.offsetLeft + " OffsetRight:" + this.$el.offsetTop)
      console.log(event)
    },
    mMove () {
      if (this.is_mousedown) {
        console.log("MOVE X:" + event.pageX + " Y:" + event.pageY)
      }
    },
    mUp () {
      if (this.is_mousedown) {
        this.is_mousedown = false
        console.log("UP X:" + event.pageX + " Y:" + event.pageY)
      }
    }
  }
};
</script>
<style scoped>
.buttons {
  margin-top: 35px;
}
.ghost {
  opacity: 0.5;
  background: #c8ebfb;
}
</style>