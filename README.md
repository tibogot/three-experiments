# three-experiments

Interactive three.js pieces. Each folder is a single self-contained `index.html`; three.js and fonts load from public CDNs, so there is no build step.

| Project | What it is | three.js |
|---|---|---|
| [`cutout-type/`](cutout-type/) | Letters cut through a white board slide in their slots as the pointer moves. Lift, Press and Wave modes, editable text. | r165, WebGL |
| [`cutout-type-v2/`](cutout-type-v2/) | The letters sit flush and invisible in one continuous board until touched; the pointer presses or lifts parts of letters, which also slide slightly sideways and open a slot. SSGI + TRAA lighting. | r186.1, WebGPU with WebGL 2 fallback |
| [`switchboard/`](switchboard/) | A wall of 2,880 illuminated rocker switches in an oak frame. Type a message or draw by flipping switches. Day/night modes, dimmer, orbit camera. | r186.1, WebGPU with WebGL 2 fallback |

## Run locally

The pages use ES module import maps, so open them through a local server rather than `file://`:

```sh
npx serve .
# then open http://localhost:3000/switchboard/
```

## Notes

- **Switchboard night mode** gives every lit switch its own point light using `ClusteredLighting` (Forward+). That needs WebGPU (recent Chrome/Edge, Safari 26+); on WebGL 2 the lamps light their neighbours through a spill texture instead.
- Deploys as-is to GitHub Pages, Netlify or Vercel.
