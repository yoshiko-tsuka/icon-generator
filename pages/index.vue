<template>
  <div class="row">
    <div class="col-6">
      <p><img @dragstart="dStart" @drag="dMove" @dragend="dEnd" class="drag-and-drop" src="/sea.png"></p>
      <span id="dummy"></span>
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
      is_dragging: false
    }
  },
  mounted () {
    
  },
  methods: {
    dStart () {
      let el = document.getElementById( "dummy" )
      event.dataTransfer.setDragImage( el, 0, 0 )
      event.srcElement.style.position = 'absolute'
      event.srcElement.style.zIndex = 1000
      event.srcElement.style.left = event.pageX - event.srcElement.offsetWidth / 2 + 'px'
      event.srcElement.style.top = event.pageY - event.srcElement.offsetHeight / 2 + 'px'
      this.is_dragging = true
      console.log("DOWN el:" + event.srcElement + "X:" + event.pageX + " Y:" + event.pageY + " OffsetLeft:" + event.srcElement.offsetWidth + " OffsetRight:" + event.srcElement.offsetHeight)
      console.log(event.dataTransfer)
    },
    dMove () {
      if (this.is_dragging && event.pageX !== 0 && event.pageY !== 0) {
        event.srcElement.style.left = event.pageX - event.srcElement.offsetWidth / 2 + 'px'
        event.srcElement.style.top = event.pageY - event.srcElement.offsetHeight / 2 + 'px'
      }
    },
    dEnd () {
      if (this.is_dragging) {
        this.is_dragging = false
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