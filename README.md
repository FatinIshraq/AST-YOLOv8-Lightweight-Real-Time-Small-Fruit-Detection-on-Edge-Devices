# AST-YOLOv8 — Lightweight Real-Time Wild Blueberry Detection on Edge Devices

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-2.x-orange?logo=pytorch)
![Deployment](https://img.shields.io/badge/Edge-Jetson%20Xavier%20NX-76B900?logo=nvidia)
![TensorRT](https://img.shields.io/badge/TensorRT-FP16-76B900?logo=nvidia)
![Task](https://img.shields.io/badge/Task-Object%20Detection-blue)
![Status](https://img.shields.io/badge/Paper-Under%20Review-yellow)

A custom lightweight YOLOv8 architecture for real-time wild blueberry detection in precision agriculture, designed for deployment on resource-constrained edge devices. AST-YOLOv8 achieves **0.934 mAP@50** with only **1.26M parameters** — running at **50+ FPS** on NVIDIA Jetson Xavier NX with a **4.2MB** TensorRT engine.

> 📄 **This repository accompanies a paper currently under review.**
> Full model code, training configurations, and dataset will be released upon paper acceptance.

---

## Highlights

| Metric | AST-YOLOv8 |
|--------|-----------|
| Parameters | **1.26M** |
| GFLOPs | **5.6** |
| mAP@50 (berry) | **0.934** |
| Inference speed (Jetson Xavier NX, TensorRT FP16) | **50.84 FPS** |
| Engine size | **4.2 MB** |

Designed for in-field deployment: small enough to run on embedded hardware mounted on agricultural robots and UAVs, fast enough for real-time decision-making during harvest assessment.

---

## Why This Matters

Wild blueberry yield estimation currently relies on manual sampling — slow, labor-intensive, and spatially sparse. Real-time berry detection from camera feeds enables:

- **Automated yield mapping** across entire fields
- **Harvest timing optimization** based on ripeness distribution
- **Input for precision management** — variable-rate application driven by fruit density

The challenge: standard detectors are too heavy for edge hardware in the field, and small berries (often <20px) are notoriously difficult for lightweight models. AST-YOLOv8 addresses both.

---

## Architectural Contributions

AST-YOLOv8 modifies the YOLOv8 architecture with four components targeting small-object detection under a strict parameter budget:

1. **ASGF-C2f** — an adaptive spatial-gated feature module replacing standard C2f blocks, with depth-aware feature weighting
2. **TinyDetectHead** — a dedicated high-resolution detection head with a spatial extraction path for small objects
3. **DF-CIoU Loss** — a modified localization loss improving bounding box regression for densely clustered small fruit
4. **SE Channel Attention** — channel recalibration at key fusion points

> Detailed architecture diagrams, module designs, and ablation studies are in the paper and will be released with the code upon acceptance.

---

## Results Preview

<img width="975" height="558" alt="image" src="https://github.com/user-attachments/assets/21118108-22c6-4244-9188-5ab741ba91eb" />


### Edge Deployment Pipeline

```
PyTorch (.pt) → ONNX → TensorRT FP16 (.engine) → Jetson Xavier NX
   1.26M params              4.2 MB engine          50.84 FPS
```

## Repository Status

| Component | Status |
|-----------|--------|
| README + benchmark results | ✅ Available now |
| Detection demo visuals | ✅ Available now |
| Model architecture code | 🔒 Released upon paper acceptance |
| Training configurations | 🔒 Released upon paper acceptance |
| Custom blueberry dataset | 🔒 Released upon paper acceptance |
| TensorRT deployment scripts | 🔒 Released upon paper acceptance |


