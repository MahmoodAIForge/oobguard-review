# OOBGuard Review

A browser page for checking OOBGuard's out-of-body redaction on a surgical video and recording a reviewer's judgement.

**Open it:** https://mahmoodaiforge.github.io/oobguard-review/

- The video is analysed on your own computer. Nothing is uploaded.
- Both frozen OOBGuard policies run: primary (P ≥ 0.001487) and guarded (P ≥ 0.000527, widened ±1 s).
- Play the video with either blackout, jump to the edges of each blacked-out stretch, and rate it.
- Press **Download CSV** and send the file to the study team.
- Press **Download redacted video** for an MP4 with the chosen blackout burned in (audio removed). The page then decodes the copy again and checks every frame: requested frames must be black and no others.

Works best in current Chrome or Edge (WebGPU). Other browsers run the model on the processor, which is slower. Use H.264 MP4 files.

## Contents

| Path | What it is |
|---|---|
| `index.html` | The page |
| `model/` | OOBGuard as ONNX: DINOv2 ViT-S/14 encoder (split into 7 parts) and the temporal head, released weights, seed 2027 |
| `runtime/` | ONNX Runtime Web 1.22.0 WebAssembly binary (split into 2 parts), MIT licence |

The page also loads mp4box.js 0.5.2 and mp4-muxer 5.2.2 from jsDelivr.

The browser decodes video slightly differently from the research pipeline, so probabilities can differ a little from the OOBGuard command-line tool. On a test clip, every primary and guarded decision matched the reference pipeline.

## Use

Research prototype for academic evaluation. It is not a medical device and does not replace human review before a video is shared. Only share a downloaded copy after the page reports that its frame check passed.

Model weights are provided for research use only.
