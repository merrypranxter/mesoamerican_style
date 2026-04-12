# Shader Hints — Mesoamerican Style

## Core Shader Mapping Ideas

### Signed Distance Fields (SDF)
- Build glyph blocks, step-fret patterns, and feather fans from SDF primitives (rectangles, circles, unions, subtractions)
- Round SDF corners slightly for Maya style; keep sharp for Aztec/Zapotec
- Use SDF edge distance to drive the pigment-in-recesses color shift

### Relief Carving Simulation
1. Construct an SDF for the design
2. Convert SDF to a height map (smooth sigmoid function)
3. Derive normals from height gradient (central differences)
4. Apply directional raking light (low angle, e.g., `lightDir = normalize(vec3(1.0, 0.3, 0.5))`)
5. Add ambient occlusion approximation by using height to darken recesses

### Pigment-in-Recesses
```glsl
float recesses = 1.0 - smoothstep(-0.1, 0.3, height);
vec3 color = mix(pigmentColor, stoneColor, recesses);
```

### Chisel Noise
- Add anisotropic noise aligned along surface tangent direction
- Use a stretched FBM with aspect ratio ~5:1 (along tool stroke direction)
- Apply only at edges (where SDF gradient is steep)

---

## Culture-Specific Shader Modules

### `aztecCodexFlat(uv)` — Codex-style flat graphic
- No SDF/height needed — pure 2D
- Strong black outline threshold on pattern shapes
- Flat color zones: no gradients
- Step-fret or xicalcoliuhqui pattern as primary element
- Parameters: `outlineWidth`, `fillColor`, `outlineColor`

### `stepFret(p, scale, ratio)` → distance
- Returns SDF distance for a repeating step-fret meander
- `scale`: unit size of one step-fret unit
- `ratio`: aspect ratio of horizontal vs. vertical steps (default 1.0 for square steps)
- Mirror about x=0 for symmetric band

### `xicalcoliuhqui(p, scale)` → distance
- Step-fret but with a rounded curl at the inner corner
- Construct as step-fret SDF minus a small circle at the turn position
- Returns smooth SDF

### `mayanGlyphBlock(uv, seed)` → color
- Subdivides a [0,1]² tile into a 3-zone cartouche
- Main sign (60% area center): fills with recursive curves/hooks using `seed` parameter
- Superfix (top-left 20%): small abstract element
- Subfix (bottom-right 20%): small abstract element
- Rounded border channel around entire block

### `interlockingScroll(uv, scale)` → float
- Two S-curves interlocked at midpoints
- Construct as: `sin(uv.x * PI) + sin(uv.y * PI)` threshold creates a starting approximation
- Add secondary frequency: `0.5 * sin(2 * uv.x * PI) + 0.5 * sin(2 * uv.y * PI)` 
- Apply SDF smoothing for proper scroll shape

### `tlaloc_goggle(p, center, radius)` → float
- Concentric ring SDF: `abs(length(p - center) - radius)` threshold for goggle ring
- Two overlapping goggle units (left eye, right eye) at fixed offset
- Below: fanged jaw using rectangle + inverted arc unions

### `featherFan(p, numFeathers, spreadAngle)` → float
- Radial array of tapered ellipses (SDF of elongated ellipse)
- Each feather: angle = `i * spreadAngle / numFeathers`, scaled from center
- Add small eye-circle near tip of each feather for quetzal eye spots
- `mix(jadeGreen, lightGreen, pow(t, 0.5))` for tip-to-base color gradient

### `pyramidProfile(p, numSteps, taludRatio)` → float
- SDF of a stepped pyramid silhouette
- Each step: a slightly wider rectangle stacked below the previous
- `taludRatio`: ratio of sloped face width to vertical panel width
- Returns silhouette SDF; use for masking or as base shape

### `cartoucheFrame(uv, borderWidth, cornerRadius)` → float
- Rounded rectangle ring: `abs(sdRoundRect(uv, size, cornerRadius)) - borderWidth`
- Used to frame glyph blocks, compositions, deity scenes
- Nest multiple cartouche frames for bordered-border compositions

---

## Animation Suggestions

### Ritual Time Drift
```glsl
float phase = sin(time * 0.3 + uv.x * 2.0) * 0.1;
// Slow oscillation in pigment intensity — like ritual torch lighting
float pigmentIntensity = pigmentInRecesses + phase * 0.05;
```

### Stone Erosion
```glsl
float erosion = smoothstep(0.0, 1.0, time * 0.01); // very slow
float reliefDepth = max(0.0, reliefMax - erosion * reliefMax);
float edgeNoise = fbm(uv * 20.0) * erosion * 0.3;
// Increase edge roughness over time; reduce relief depth
```

### Glyph Reveal / Inscription
```glsl
float reveal = smoothstep(startTime, startTime + duration, time);
float glyphAlpha = step(uv.x, reveal); // left-to-right reveal
// Or use SDF with expanding threshold: step(sdfValue, reveal * maxDist)
```

### Calendar Wheel Rotation
```glsl
float angle = time * 0.1; // slow ritual rotation
vec2 rotatedUV = mat2(cos(angle), -sin(angle), sin(angle), cos(angle)) * (uv - 0.5);
// Apply day-sign ring sampling to rotatedUV
```

---

## Lighting Models for Stone Relief

### Raking Light (Primary)
```glsl
vec3 lightDir = normalize(vec3(1.0, 0.5, 0.3)); // low angle from side
float diffuse = max(0.0, dot(normal, lightDir));
float ambient = 0.15;
float light = ambient + (1.0 - ambient) * diffuse;
```

### Groove Shadow (Ambient Occlusion Proxy)
```glsl
// Use SDF distance from nearest edge as AO proxy
float ao = smoothstep(-0.05, 0.2, sdf);
// ao = 0 in deep grooves, 1 on open surfaces
```

### Pigment Accumulation
```glsl
// Pigment collects in deepest recesses (lowest ao)
vec3 surfaceColor = mix(pigmentColor, stoneColor, pow(ao, 0.5));
// Apply lighting on top
surfaceColor *= light;
```

### Multi-Layer Stone Patina
```glsl
vec3 fresh = stoneBaseColor;
vec3 patina = mix(stoneBaseColor, vec3(0.5, 0.48, 0.42), 0.4); // grey-green patina
float patinaAmt = smoothstep(0.3, 0.8, fbm(uv * 5.0)); // irregular patina coverage
vec3 surfaceColor = mix(fresh, patina, patinaAmt);
```

