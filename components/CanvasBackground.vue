<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const config = { // Configuration object
  // numPoints ahora es un objeto con valores por breakpoint
  numPoints: { mobile: 80, tablet: 150, desktop: 350 }, // Aumentado para desktop
  connectionRadius: 100, distortionRadius: 90, distortionStrength: 45,
  defaultLineColorBase: '75, 85, 99', accentLineColorBase: '168, 85, 247',
  accentLineProbability: 0.07, baseSpeed: 0.2, speedVariation: 0.1, wanderStrength: 0.003,
  lineWidth: 0.7, resizeDebounceMs: 150, minLineOpacity: 0.2, defaultLineAlpha: 0.5, accentLineAlpha: 0.6,
  // Breakpoints (adjust as needed)
  tabletBreakpoint: 768,
  desktopBreakpoint: 1024
};

const canvasRef = ref(null); // Canvas reference
let ctx = null, points = [], mouse = { x: null, y: null }, animationFrameId = null, resizeTimeout = null; // State variables
let currentNumPoints = config.numPoints.desktop; // Default to desktop, will be updated on mount/resize

class Point { // Point class definition
  constructor(x, y, w, h) { Object.assign(this, { x, y, w, h, originalX: x, originalY: y, vx: (Math.random() - 0.5) * config.baseSpeed * 2, vy: (Math.random() - 0.5) * config.baseSpeed * 2 }); }
  update() {
    this.vx += (Math.random() - 0.5) * config.wanderStrength; this.vy += (Math.random() - 0.5) * config.wanderStrength;
    const speed = Math.hypot(this.vx, this.vy), maxSpeed = config.baseSpeed + config.speedVariation;
    if (speed > maxSpeed) { const ratio = maxSpeed / speed; this.vx *= ratio; this.vy *= ratio; }
    this.x += this.vx; this.y += this.vy;
    if (mouse.x !== null) {
      const dx = this.x - mouse.x, dy = this.y - mouse.y, dist = Math.hypot(dx, dy);
      if (dist < config.distortionRadius && dist > 0) { const force = (1 - dist / config.distortionRadius) * config.distortionStrength * 0.1; this.x += (dx / dist) * force; this.y += (dy / dist) * force; }
    }
    const m = config.connectionRadius; // Boundary check
    if (this.x < -m) this.x = this.w + m; else if (this.x > this.w + m) this.x = -m;
    if (this.y < -m) this.y = this.h + m; else if (this.y > this.h + m) this.y = -m;
  }
}

// initPoints ahora acepta el número de puntos a crear
const initPoints = (c, numPts) => Array.from({ length: numPts }, () => new Point(Math.random() * c.width, Math.random() * c.height, c.width, c.height)); // Initialize points

function drawLines(ct, pts) { // Draw connecting lines
  if (!ct || !pts) return; ct.lineWidth = config.lineWidth;
  for (let i = 0; i < pts.length; i++) {
    for (let j = i + 1; j < pts.length; j++) {
      const p1 = pts[i], p2 = pts[j], dist = Math.hypot(p1.x - p2.x, p1.y - p2.y);
      if (dist < config.connectionRadius) {
        const opacity = Math.max(config.minLineOpacity, 1 - (dist / config.connectionRadius));
        const isAccent = Math.random() < config.accentLineProbability;
        ct.strokeStyle = `rgba(${isAccent ? config.accentLineColorBase : config.defaultLineColorBase}, ${(isAccent ? config.accentLineAlpha : config.defaultLineAlpha) * opacity})`;
        ct.beginPath(); ct.moveTo(p1.x, p1.y); ct.lineTo(p2.x, p2.y); ct.stroke();
      }
    }
  }
}

function animate() { // Animation loop
  const c = canvasRef.value; if (!ctx || !c) { cancelAnimationFrame(animationFrameId); animationFrameId = null; return; }
  ctx.clearRect(0, 0, c.width, c.height); points.forEach(p => p.update()); drawLines(ctx, points);
  animationFrameId = requestAnimationFrame(animate);
}

const handleResize = () => { // Handle window resize
  const c = canvasRef.value; if (!c) return;
  const width = window.innerWidth || 800;
  const height = window.innerHeight || 600;
  c.width = width; c.height = height;

  // Determinar el número de puntos según el ancho
  if (width < config.tabletBreakpoint) {
      currentNumPoints = config.numPoints.mobile;
  } else if (width < config.desktopBreakpoint) {
      currentNumPoints = config.numPoints.tablet;
  } else {
      currentNumPoints = config.numPoints.desktop; // Usará el valor actualizado (350)
  }

  ctx = c.getContext('2d'); if (!ctx) return console.error("No 2D context");
  // No es necesario actualizar w/h en puntos existentes si los reinicializamos siempre
  points = initPoints(c, currentNumPoints); // Update points using the selected number
};
const debouncedResize = () => { clearTimeout(resizeTimeout); resizeTimeout = setTimeout(handleResize, config.resizeDebounceMs); }; // Debounced resize

onMounted(() => { // Setup on component mount
  if (typeof window === 'undefined') return; const c = canvasRef.value; if (!c || !c.getContext) return; ctx = c.getContext('2d'); if (!ctx) return;
  handleResize(); // Llama a handleResize para establecer tamaño y número inicial de puntos
  if (ctx && points.length > 0) animate();
  document.addEventListener('mousemove', (e) => { mouse.x = e.clientX; mouse.y = e.clientY; });
  document.documentElement.addEventListener('mouseleave', () => { mouse.x = null; mouse.y = null; });
  window.addEventListener('resize', debouncedResize);
});

onUnmounted(() => { // Cleanup on component unmount
  if (typeof window === 'undefined') return; cancelAnimationFrame(animationFrameId); clearTimeout(resizeTimeout);
  animationFrameId = null; resizeTimeout = null; window.removeEventListener('resize', debouncedResize);
  // Note: Inline mousemove/mouseleave listeners are not removed here for brevity.
});
</script>

<template>
  <canvas ref="canvasRef" class="canvas-background"></canvas> </template>

<style scoped>
.canvas-background { display: block; position: fixed; top: 0; left: 0; width: 100%; height: 100%; z-index: -1; pointer-events: none; } /* Basic styling */
</style>
  