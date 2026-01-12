<template>
  <canvas ref="canvas"></canvas>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const canvas = ref(null)

const pixelSize = 10

const teto = [
  [0,0,1,0,0,0,1,0,0],
  [0,1,1,1,0,1,1,1,0],
  [0,0,1,1,1,1,1,0,0],
  [0,1,1,1,1,1,1,1,0],
  [1,1,1,1,1,1,1,1,1],
  [1,1,1,0,1,0,1,1,1],
  [1,1,1,1,1,1,1,1,1],
  [0,0,0,1,1,1,0,0,0],
  [0,0,1,1,1,1,1,0,0],
  [0,1,1,1,1,1,1,1,0],
  [1,1,1,1,1,1,1,1,1],
  [0,1,1,0,0,0,1,1,0],
  [1,1,1,0,0,0,1,1,1],
]

onMounted(() => {
  const ctx = canvas.value.getContext('2d')

  canvas.value.width = teto[0].length * pixelSize
  canvas.value.height = teto.length * pixelSize

  teto.forEach((row, y) => {
    row.forEach((cell, x) => {
      if (cell) {
        ctx.fillStyle = '#e06666'
        ctx.fillRect(
          x * pixelSize,
          y * pixelSize,
          pixelSize,
          pixelSize
        )
      }
    })
  })
})
</script>
