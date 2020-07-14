<template>
  <div class="row">
    <div class="col-6">
      <svg id="artboard" xmlns="http://www.w3.org/2000/svg" style="background-color:#ccc" width="500" height="500" viewbox="0 0 500 500" @mouseup="dEnd">
        <circle class="drag-and-drop" cx=30 cy=30 r=30 fill="blue" @mousedown.self.stop="mDownCircle" @mousemove.self.stpo="mMoveCircle"/>
        <rect x="100" y="150" rx="0" ry="0" width="50" height="40" stroke-width="1" stroke="#00FFFF" fill="#CCFFFF" @mousedown.self.stop="mDownSquare" @mousemove.self.stop="mMoveSquare"/>
        <line x1="100" y1="100" x2="400" y2="100" stroke-width="10" stroke="#FF00FF" @mousedown.self.stop="mDownLine" @mousemove.self.stop="mMoveLine"/>
      　<polygon points="20 30, 35 10, 50 30" stroke-width="1" stroke="#000000" fill="#FF00FF" @mousedown.self.stop="mDownPoligon" @mousemove.self.stop="mMovePoligon" />
      　<polygon points="60 30, 75 10, 90 30, 75 50" stroke-width="1" stroke="#000000" fill="#FF00FF" @mousedown.self.stop="mDownPoligon" @mousemove.self.stop="mMovePoligon" />
        <image href="/sea.png" x="300" y="300" width="50" height="40" @mousedown.self.stop="mDownSquare" @mousemove.self.stop="mMoveSquare" />
      </svg>
    </div>
    <div class="col-6">
      <div><button @click="svg2imageData">変換する</button></div>
      <img src="" id="converted-image">
      <button v-show="show" id="icon-download" type="application/octet-stream" href="" download="your_icon.png">Download</button>
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
      arr: '0 0, 0 0, 0 0',
      is_dragging: false,
      show: false
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
        this.arr = '0 0, 0 0, 0 0'
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
    },
    mDownPoligon () {
      this.is_dragging = true
      this.x = event.pageX
      this.y = event.pageY
      this.arr = event.target.attributes.points.value
    },
    mMovePoligon () {
      if (this.is_dragging && event.pageX !== 0 && event.pageY !== 0) {
        let points = ''
        const difX = event.pageX - this.x
        const difY = event.pageY - this.y
        this.arr.split(', ').forEach(function( value ) {
          const xy = value.split(' ')
          const x1 = difX + parseInt(xy[0])
          const y1 = difY + parseInt(xy[1])
          if (points === ''){
            points = x1 + ' ' + y1
          } else {
            points += ', ' + x1 + ' ' + y1
          }
        })
        event.target.setAttribute('points', points)
      }
    },
    svg2imageData () {
      const canvas = document.createElement('canvas')
      const svgElement = document.getElementById('artboard')
      console.log(svgElement)
      canvas.width = svgElement.width.baseVal.value
      canvas.height = svgElement.height.baseVal.value
      const img = document.getElementById('converted-image')
      const ctx = canvas.getContext('2d')
      
      console.log(ctx)
      const svgData = new XMLSerializer().serializeToString(svgElement)
      console.log(svgData)
      const imgsrc = 'data:image/svg+xml;charset=utf-8;base64,' + btoa(unescape(encodeURIComponent(svgData)))
      console.log(imgsrc)
      ctx.drawImage(img, 0, 0, img.width, img.height)
      const downloadBtn = document.getElementById('icon-download')
      console.log(downloadBtn)
      downloadBtn.href = canvas.toDataURL("image/png")
      img.src = imgsrc
      this.show = true
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