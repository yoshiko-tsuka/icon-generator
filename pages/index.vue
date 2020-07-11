<template>
  <div class="row">
    <div class="col-6">
      <p><img @dragstart.self="dStart" @drag.self="dMove" @dragend.self="dEnd" class="drag-and-drop" src="/sea.png"></p>
    </div>
    <div class="col-6">
      <svg xmlns="http://www.w3.org/2000/svg" style="background-color:#ccc" width="400" height="300" viewbox="0 0 400 300" @mouseup="dEnd">
        <circle class="drag-and-drop" cx=30 cy=30 r=30 fill="blue" @mousedown.self.stop="mDownCircle" @mousemove.self.stpo="mMoveCircle"/>
        <rect x="100" y="150" rx="0" ry="0" width="50" height="40" stroke-width="1" stroke="#00FFFF" fill="#CCFFFF" @mousedown.self.stop="mDownSquare" @mousemove.self.stop="mMoveSquare"/>
        <line x1="100" y1="100" x2="400" y2="100" stroke-width="10" stroke="#FF00FF" @mousedown.self.stop="mDownLine" @mousemove.self.stop="mMoveLine"/>
      　<polygon points="20 30, 35 10, 50 30" stroke-width="1" stroke="#000000" fill="none" />
      　<polygon points="60 30, 75 10, 90 30, 75 50" stroke-width="1" stroke="#000000" fill="none" />
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
      cx: 0,
      cy: 0,
      xl: 0,
      yl: 0,
      r: 0,
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
      event.target.style.position = 'absolute'
      event.target.style.zIndex = 1000
      event.target.style.left = event.pageX - event.target.offsetWidth / 2 + 'px'
      event.target.style.top = event.pageY - event.target.offsetHeight / 2 + 'px'
      this.is_dragging = true
    },
    dMove () {
      if (this.is_dragging && event.pageX !== 0 && event.pageY !== 0) {
        event.target.style.left = event.pageX - event.target.offsetWidth / 2 + 'px'
        event.target.style.top = event.pageY - event.target.offsetHeight / 2 + 'px'
      }
    },
    dEnd () {
      if (this.is_dragging) {
        this.is_dragging = false
        this.x = 0
        this.y = 0
        this.cx = 0
        this.cy = 0
        this.xl = 0
        this.yl = 0
        this.r = 0
        console.log(this.is_dragging)
      }
    },
    mDownCircle () {
      this.is_dragging = true
      this.x = event.pageX
      this.y = event.pageY
      this.cx = parseInt(event.target.attributes.cx.value)
      this.cy = parseInt(event.target.attributes.cy.value)
      this.r = parseInt(event.target.attributes.r.value) 
    },
    mMoveCircle () {
      if (this.is_dragging && event.pageX !== 0 && event.pageY !== 0) {
        console.log("move Circle")
        event.target.setAttribute('cx', event.pageX - this.x + this.cx)
        event.target.setAttribute('cy', event.pageY - this.y + this.cy)
      }
    },
    mDownSquare () {
      this.is_dragging = true
      this.x = event.pageX
      this.y = event.pageY
      this.cx = parseInt(event.target.attributes.x.value)
      this.cy = parseInt(event.target.attributes.y.value)
    },
    mMoveSquare () {
      if (this.is_dragging && event.pageX !== 0 && event.pageY !== 0) {
        console.log("move Square")
        event.target.setAttribute('x', event.pageX - this.x + this.cx)
        event.target.setAttribute('y', event.pageY - this.y + this.cy)
      }
    },
    mDownLine () {
      this.is_dragging = true
      this.x = event.pageX
      this.y = event.pageY
      this.cx = parseInt(event.target.attributes.x1.value)
      this.cy = parseInt(event.target.attributes.y1.value)
      this.xl = parseInt(event.target.attributes.x2.value) - parseInt(event.target.attributes.x1.value)
      this.yl = parseInt(event.target.attributes.y2.value) - parseInt(event.target.attributes.y1.value)
    },
    mMoveLine () {
      if (this.is_dragging && event.pageX !== 0 && event.pageY !== 0) {
        console.log("move Line")
        event.target.setAttribute('x1', event.pageX - this.x + this.cx)
        event.target.setAttribute('y1', event.pageY - this.y + this.cy)
        event.target.setAttribute('x2', event.pageX - this.x + this.cx + this.xl)
        event.target.setAttribute('y2', event.pageY - this.y + this.cy + this.yl)
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