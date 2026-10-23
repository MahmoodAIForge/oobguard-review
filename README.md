# OOBGuard Review

A browser page for checking OOBGuard's out-of-body redaction on a surgical video and recording a reviewer's judgement.

**Open it:** https://mahmoodaiforge.github.io/oobguard-review/

- The video is analysed on your own computer. Nothing is uploaded.
- Both frozen OOBGuard policies run: primary (P ≥ 0.001487) and guarded (P ≥ 0.000527, widened ±1 s).
- Play the video with either blackout, jump to the edges of each blacked-out stretch, and rate it.
- Press **Download CSV** and send the file to the study team.

Works best in current Chrome or Edge (WebGPU). Other browsers run the model on the processor, which is slower. Use H.264 MP4 files.

## Contents

| Path | What it is |
|---|---|
| `index.html` | The page |
| `model/` | OOBGuard as ONNX: DINOv2 ViT-S/14 encoder (split into 7 parts) and the temporal head, released weights, seed 2027 |
| `runtime/` | ONNX Runtime Web 1.22.0 WebAssembly binary (split into 2 parts), MIT licence |

The browser decodes video slightly differently from the research pipeline, so probabilities can differ a little from the OOBGuard command-line tool. On a test clip, every primary and guarded decision matched the reference pipeline.

## Use

Research prototype for academic evaluation. It is not a medical device and does not replace human review before a video is shared. The blackout on the page is a preview; make release copies with the OOBGuard command-line tool, which verifies every frame of the output.

Model weights are provided for research use only.
