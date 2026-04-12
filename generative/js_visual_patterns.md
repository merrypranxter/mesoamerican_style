# JavaScript Visual Patterns — Mesoamerican Style

## Core Abstractions

### Layout System
```javascript
function makeGrid(w, h, cellSize) {
  const cols = Math.floor(w / cellSize);
  const rows = Math.floor(h / cellSize);
  return { cols, rows, cellSize };
}

function quantize(v, step) {
  return Math.round(v / step) * step;
}

function mirrorX(points) {
  return [...points, ...points.map(([x, y]) => [-x, y]).reverse()];
}

function registerBands(totalHeight, numBands, bandRatios) {
  // bandRatios: array of relative heights; normalizes to totalHeight
  const sum = bandRatios.reduce((a, b) => a + b, 0);
  let y = 0;
  return bandRatios.map(ratio => {
    const h = (ratio / sum) * totalHeight;
    const band = { y, height: h };
    y += h;
    return band;
  });
}
```

### Color Utilities
```javascript
// Load palette by id from palettes.json
function getPalette(id, palettes) {
  return palettes.find(p => p.id === id)?.colors || [];
}

function hexToRgb(hex) {
  const r = parseInt(hex.slice(1,3), 16);
  const g = parseInt(hex.slice(3,5), 16);
  const b = parseInt(hex.slice(5,7), 16);
  return { r, g, b };
}

function recessColor(baseHex, pigmentHex, recedAmount) {
  // Mix base stone color with pigment at given recess depth
  const base = hexToRgb(baseHex);
  const pigment = hexToRgb(pigmentHex);
  return {
    r: base.r + (pigment.r - base.r) * recedAmount,
    g: base.g + (pigment.g - base.g) * recedAmount,
    b: base.b + (pigment.b - base.b) * recedAmount,
  };
}
```

---

## Pattern Generators

### Step-Fret Border Band
```javascript
function drawStepFretBand(ctx, x, y, width, height, numUnits, mirrored = true) {
  const unitW = width / numUnits;
  const step = unitW / 4; // one step unit
  ctx.beginPath();
  for (let i = 0; i < numUnits; i++) {
    const ox = x + i * unitW;
    // Draw one step-fret unit: a quantized L-path
    ctx.moveTo(ox, y + height);
    ctx.lineTo(ox, y + step);
    ctx.lineTo(ox + step, y + step);
    ctx.lineTo(ox + step, y);
    ctx.lineTo(ox + step * 2, y);
    ctx.lineTo(ox + step * 2, y + step * 2);
    ctx.lineTo(ox + step * 3, y + step * 2);
    ctx.lineTo(ox + step * 3, y + height);
    ctx.closePath();
  }
  ctx.fill();
}
```

### Glyph Block Tile
```javascript
function drawGlyphBlock(ctx, x, y, size, seed) {
  const rng = mulberry32(seed);
  // Outer cartouche (rounded rect)
  const r = size * 0.08;
  ctx.roundRect(x, y, size, size, r);
  ctx.stroke();
  // Inner border channel
  const margin = size * 0.12;
  ctx.roundRect(x + margin, y + margin, size - 2*margin, size - 2*margin, r * 0.5);
  ctx.stroke();
  // Internal subdivision — 3×3 implied grid
  const cell = (size - 2*margin) / 3;
  const numSubElements = Math.floor(rng() * 3) + 2;
  for (let i = 0; i < numSubElements; i++) {
    const ex = x + margin + Math.floor(rng() * 3) * cell;
    const ey = y + margin + Math.floor(rng() * 3) * cell;
    // Draw hook, S-curve, or dot at each cell
    const type = Math.floor(rng() * 3);
    if (type === 0) drawHook(ctx, ex, ey, cell, rng);
    else if (type === 1) drawSCurve(ctx, ex, ey, cell, rng);
    else ctx.arc(ex + cell/2, ey + cell/2, cell * 0.25, 0, Math.PI * 2);
  }
}
```

### Xicalcoliuhqui Scroll-Fret
```javascript
function drawXicalcoliuhqui(ctx, x, y, unitSize) {
  const s = unitSize;
  const r = s * 0.2; // scroll radius
  ctx.beginPath();
  ctx.moveTo(x, y + s);
  ctx.lineTo(x, y + s * 0.3);
  ctx.lineTo(x + s * 0.3, y + s * 0.3);
  ctx.lineTo(x + s * 0.3, y + r); // transition to scroll
  ctx.arcTo(x + s * 0.3, y, x + s * 0.3 + r, y, r); // the scroll curl
  ctx.lineTo(x + s, y);
  ctx.lineTo(x + s, y + s);
  ctx.closePath();
}
```

### Interlocking Scroll Pattern (Veracruz)
```javascript
function drawInterlockingScrollFill(ctx, width, height, scale) {
  for (let row = 0; row * scale < height; row++) {
    for (let col = 0; col * scale < width; col++) {
      const flip = (row + col) % 2 === 0;
      drawScrollUnit(ctx, col * scale, row * scale, scale, flip);
    }
  }
}

function drawScrollUnit(ctx, x, y, s, flip) {
  ctx.save();
  if (flip) {
    ctx.translate(x + s, y + s);
    ctx.rotate(Math.PI);
  } else {
    ctx.translate(x, y);
  }
  ctx.beginPath();
  // S-curve: two arcs
  ctx.arc(s * 0.25, s * 0.5, s * 0.25, Math.PI * 0.5, Math.PI * 1.5);
  ctx.arc(s * 0.75, s * 0.5, s * 0.25, Math.PI * 1.5, Math.PI * 0.5);
  ctx.stroke();
  ctx.restore();
}
```

### Feather Fan
```javascript
function drawFeatherFan(ctx, cx, cy, numFeathers, maxLen, spreadRad) {
  const angleStep = spreadRad / (numFeathers - 1);
  const startAngle = -spreadRad / 2;
  for (let i = 0; i < numFeathers; i++) {
    const angle = startAngle + i * angleStep;
    const len = maxLen * (0.7 + 0.3 * Math.cos(i * Math.PI / (numFeathers - 1)));
    const tipX = cx + Math.cos(angle) * len;
    const tipY = cy + Math.sin(angle) * len;
    // Tapered feather stroke
    ctx.beginPath();
    ctx.moveTo(cx, cy);
    ctx.quadraticCurveTo(
      cx + Math.cos(angle) * len * 0.6 + Math.cos(angle + Math.PI/2) * 5,
      cy + Math.sin(angle) * len * 0.6 + Math.sin(angle + Math.PI/2) * 5,
      tipX, tipY
    );
    ctx.lineWidth = Math.max(0.5, 3 * (1 - i / numFeathers));
    ctx.stroke();
    // Quetzal eye spot near tip
    ctx.beginPath();
    ctx.arc(tipX - Math.cos(angle) * 8, tipY - Math.sin(angle) * 8, 2, 0, Math.PI * 2);
    ctx.fill();
  }
}
```

---

## Composition Templates

### Register Band Composition (Codex-style)
```javascript
function drawCodexPage(ctx, w, h, bands) {
  // bands: [{motifFn, palette, heightRatio}, ...]
  const bh = h / bands.length;
  bands.forEach((band, i) => {
    const y = i * bh;
    ctx.fillStyle = band.palette.background;
    ctx.fillRect(0, y, w, bh);
    // Draw horizontal border lines separating registers
    ctx.strokeStyle = band.palette.border || '#1A1208';
    ctx.lineWidth = 2;
    ctx.strokeRect(0, y, w, bh);
    // Execute the band's motif function
    band.motifFn(ctx, 0, y, w, bh, band.palette);
  });
}
```

### Glyph Wall (Maya-style horror vacui)
```javascript
function drawGlyphWall(ctx, x, y, w, h, blockSize, palette) {
  const cols = Math.floor(w / blockSize);
  const rows = Math.floor(h / blockSize);
  // Paired columns reading order: L-R in pairs, T-B
  for (let row = 0; row < rows; row++) {
    for (let col = 0; col < cols; col++) {
      const seed = row * 997 + col * 31 + 7;
      ctx.strokeStyle = palette.outline;
      ctx.fillStyle = palette.background;
      const bx = x + col * blockSize;
      const by = y + row * blockSize;
      drawGlyphBlock(ctx, bx, by, blockSize, seed);
    }
  }
}
```

### Sun Stone Concentric Rings
```javascript
function drawSunStone(ctx, cx, cy, outerR, palette) {
  const rings = [
    { r: outerR * 0.12, motif: 'deity_face' },
    { r: outerR * 0.25, motif: 'four_cartouches' },
    { r: outerR * 0.50, motif: 'day_signs_20' },
    { r: outerR * 0.65, motif: 'sky_band' },
    { r: outerR * 0.78, motif: 'jade_dots' },
    { r: outerR * 0.90, motif: 'sun_rays' },
    { r: outerR * 1.00, motif: 'serpent_frame' },
  ];
  rings.forEach((ring, i) => {
    ctx.beginPath();
    ctx.arc(cx, cy, ring.r, 0, Math.PI * 2);
    ctx.strokeStyle = palette.groove;
    ctx.lineWidth = 1.5;
    ctx.stroke();
    // Fill ring band with motif (per ring.motif type)
    const innerR = i > 0 ? rings[i-1].r : 0;
    drawRingMotif(ctx, cx, cy, innerR, ring.r, ring.motif, palette);
  });
}
```

---

## Generative Constraints

### Culture-Specific Constraint Sets
```javascript
const constraints = {
  aztec: {
    palette: 'aztec_codex',
    borderMotif: 'xicalcoliuhqui',
    symmetry: 0.9,
    strokeWeight: 'heavy',
    gradients: false,
    glyphStyle: 'aztec_pictographic',
  },
  maya: {
    palette: 'maya_polychrome',
    borderMotif: 'cauac_sky_band',
    symmetry: 0.7,
    strokeWeight: 'medium',
    horrorVacui: true,
    glyphStyle: 'maya_hieroglyphic',
  },
  olmec: {
    palette: 'olmec_stone_jade',
    borderMotif: 'trefoil_organic',
    symmetry: 1.0,
    strokeWeight: 'none', // no outlines — 3D mass
    smooth: true,
    style: '3d_sculptural',
  },
  teotihuacan: {
    palette: 'teotihuacan_mural',
    layout: 'horizontal_registers',
    borderMotif: 'step_fret',
    figureOrientation: 'frontal',
    backgroundFill: 'water_drops',
  },
  veracruz: {
    palette: 'gulf_coast_scroll',
    borderMotif: 'interlocking_scroll',
    fillPattern: 'interlocking_scroll',
    scrollCurvature: 1.0,
    energy: 'high', // dynamic, not static
  },
};
```

### RNG Utility (for deterministic seeds)
```javascript
function mulberry32(seed) {
  return function() {
    seed |= 0; seed = seed + 0x6D2B79F5 | 0;
    let t = Math.imul(seed ^ seed >>> 15, 1 | seed);
    t = t + Math.imul(t ^ t >>> 7, 61 | t) ^ t;
    return ((t ^ t >>> 14) >>> 0) / 4294967296;
  };
}
```

