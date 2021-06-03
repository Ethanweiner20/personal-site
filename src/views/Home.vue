<template>
  <div id="home">
    <canvas id="canvas"></canvas>

    <div id="main" class="ps-sm-3 p-md-5">
      <div class="layer row" id="layer-1">
        <h1 class="main-node display-1" id="name">ETHAN WEINER</h1>
      </div>
      <div class="layer row" id="layer-2">
        <div class="col-4 py-auto px-auto">
          <router-link :to="{ name: 'About' }"
            ><h3 class="node mx-auto" id="about">About</h3></router-link
          >
        </div>
        <div class="col-4 py-auto px-auto">
          <router-link :to="{ name: 'Projects' }"
            ><h3 class="node mx-auto" id="portfolio">Portfolio</h3></router-link
          >
        </div>
        <div class="col-4 py-auto px-auto">
          <router-link :to="{ name: 'Contact' }"
            ><h3 class="node mx-auto" id="contact">Contact</h3></router-link
          >
        </div>
      </div>
      <div class="layer row" id="layer-3">
        <div class="col-6 py-auto px-auto">
          <router-link :to="{ name: 'Projects' }"
            ><h3 class="node mx-auto" id="projects-heading">
              Projects
            </h3></router-link
          >
        </div>
        <div class="col-6 py-auto px-auto">
          <router-link :to="{ name: 'Skills' }"
            ><h3 class="node mx-auto" id="skills">Skills</h3></router-link
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import { onMounted } from '@vue/runtime-core'

export default {
  name: 'Home',
  setup() {
    onMounted(() => {
      // Set up canvas
      var canvas = document.getElementById('canvas')
      canvas.style.width = window.innerWidth + 'px'
      canvas.style.height = window.innerHeight + 'px'
      var ctx = canvas.getContext('2d')

      // Length of layers in the tree
      const LAYER_HEIGHT = 150

      // Resize the canvas to fill browser window dynamically
      window.addEventListener('resize', resizeCanvas, false)

      function resizeCanvas() {
        canvas.style.width = window.innerWidth + 'px'
        canvas.style.height = window.innerHeight + 'px'
        canvas.width = window.innerWidth
        canvas.height = window.innerHeight

        drawLines()
        drawTree()
      }

      function drawLines() {
        const origin_y =
          (document.querySelector('#name').getBoundingClientRect().top +
            document.querySelector('#name').getBoundingClientRect().bottom) /
          2

        ctx.strokeStyle = '#666666'
        ctx.lineWidth = 0.5

        // Draw lines protruding from name to outer edges
        for (let angle = 0; angle < 360; angle += 7.5) {
          drawLine_Angle(angle, origin_y)
        }
      }

      function drawTree(activeNodes) {
        drawLayer(document.querySelector('#name'), 2, activeNodes)
        drawLayer(document.querySelector('#portfolio'), 3, activeNodes)
      }
      // Draws the actual tree structure
      // Idea: Given a starting _node_, draw lines to the nodes in the current _layer_
      function drawLayer(node, layer, activeNodes) {
        ctx.lineWidth = 2

        let start = {
          x: window.innerWidth / 2,
          y: node.getBoundingClientRect().bottom
        }

        document
          .querySelector(`#layer-${layer}`)
          .querySelectorAll('.node')
          .forEach((node) => {
            if (activeNodes && activeNodes.includes(node))
              ctx.strokeStyle = '#FFFFFF'
            else ctx.strokeStyle = 'rgb(121, 5, 255)'
            // Determine average value of right & left to get center of node
            let x =
              (node.getBoundingClientRect().left +
                node.getBoundingClientRect().right) /
              2
            let y = node.getBoundingClientRect().top

            drawLine(start, { x, y })
          })
      }

      // drawLine : Number -> _
      // Draws a line on the canvas from the center of the screen at _angle_, all the way through to the outer edges

      function drawLine_Angle(angle, origin_y) {
        // generateStart : Number -> Posn
        // Generates where to draw the start depending on _angle_ (either top or bottom of center text)
        const start = {
          x: window.innerWidth / 2, // x is center of the screen
          y: origin_y // y is the top of the name
        }

        // generateEnd : Posn Number -> Posn
        // Generates the endpoint of a particular line based on _start_ and _angle_

        const generateEnd = () => {
          var x = innerWidth / 2
          var y = origin_y

          // Edge cases for the slope
          if (angle == 90) {
            y = 0
          } else if (angle == 270) {
            y = window.innerHeight
          } else {
            let slope = Math.tan((angle * Math.PI) / 180)
            // If angle is in quadrant I or IV, x should change by a positive value
            let deltaX =
              (0 <= angle && angle < 90) || (270 < angle && angle < 360)
                ? 10
                : -10 // Arbitrary deltaX to help compute
            let deltaY = -deltaX * slope
            // Increment x, y by _slope_ until we hit edges
            while (
              x > 0 &&
              x < window.innerWidth &&
              y > 0 &&
              y < window.innerHeight
            ) {
              x += deltaX
              y += deltaY
            }
          }

          return { x, y }
        }

        let end = generateEnd()

        drawLine(start, end)
      }

      function drawLine(start, end) {
        ctx.beginPath()
        ctx.moveTo(start.x, start.y)
        ctx.lineTo(end.x, end.y)

        // Draw the lines
        ctx.stroke()
      }

      // Initialize the Canvas
      setTimeout(resizeCanvas, 1500)

      // Watch for changes to nodes
      document.querySelectorAll('.node').forEach((node) => {
        node.addEventListener('mouseover', () => {
          drawTree([node])
        })
        node.addEventListener('mouseleave', () => {
          drawTree()
        })
      })
    })
  }
}
</script>

<style lang="scss">
@import '@/assets/styles.scss';

@keyframes fadeCanvas {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

#canvas {
  opacity: 1;
  animation: fadeCanvas 3s ease 1s;
}

#home {
  display: flex;
  justify-content: center;
  align-items: center;

  margin: 0;
}

a {
  text-decoration: none !important;
}

.node {
  border: 3px solid $main-color;
  padding: 15px;
  height: 70px;
  background-color: $main-dark;
  width: 150px;
  text-align: center;
  border-radius: 50px;
  color: white;

  @media (max-width: 600px) {
    width: 125px;
  }

  @media (max-width: 420px) {
    height: 60px;
    width: 110px;
    padding: 10px;
  }

  &:hover {
    color: $main-color;
    background-color: white;
    border-color: white;
    transition: background-color 1s ease, color 1s ease, width 1s ease,
      border-color 1s ease;
    width: 170px;
    cursor: pointer;
  }
}
.main-node {
  border: none;
  background-color: transparent;
  height: 60px;
  padding-top: 5px;
  font-size: 55px;
}
#name {
  height: 80px;
}
#main {
  position: absolute;
  max-width: 800px;
  color: white;
  @media (max-width: 600px) {
    width: 100%;
    font-size: 15px !important;
  }
}
.layer {
  height: 200px;
}
</style>
