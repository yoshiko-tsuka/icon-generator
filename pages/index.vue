<template>
  <div class="row">
    <div class="col-6">
      <p><img @dragstart="dStart" @drag="dMove" @dragend="dEnd" class="drag-and-drop" src="/sea.png"></p>
    </div>
    <div class="col-6">
      <svg xmlns="http://www.w3.org/2000/svg" width="300" height="300" viewBox="0 0 300 300" style="background-color: #ccc">
        <circle class="drag-and-drop" cx=100 cy=50 r=30 @mousedown="mDown" @mousemove="dMove" @mouseup="dEnd"/>
      </svg>
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
      var dragImage = document.createElement('img');
      dragImage.src = '/DragImage.png';
      event.dataTransfer.setDragImage( dragImage, 0, 0 )
      event.srcElement.style.position = 'absolute'
      event.srcElement.style.zIndex = 1000
      event.srcElement.style.left = event.pageX - event.srcElement.offsetWidth / 2 + 'px'
      event.srcElement.style.top = event.pageY - event.srcElement.offsetHeight / 2 + 'px'
      this.is_dragging = true
      console.log("Start!")
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
      }
    },
    mDown () {
      event.srcElement.style.position = 'absolute'
      event.srcElement.style.zIndex = 1000
      event.srcElement.style.left = event.pageX - event.srcElement.offsetWidth / 2 + 'px'
      event.srcElement.style.top = event.pageY - event.srcElement.offsetHeight / 2 + 'px'
      this.is_dragging = true
      console.log("Start!")
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