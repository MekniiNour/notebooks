# notebooks
# WasteVision Pipeline – Modular AI for Waste Detection and Analysis

> Developed at **Esprit School of Engineering** as part of the GitHub Education initiative, this notebook implements a complete, modular AI pipeline for automated waste image analysis using object detection, multimodal inference, and explainable AI techniques.

---

## Project Description

This project, **WasteVision Pipeline**, was created as part of an applied AI engineering course at _Esprit School of Engineering_. It showcases an end-to-end system for detecting and analyzing waste in images using modern AI tools. The notebook performs:
- Object detection with YOLOv8
- Attribute inference (material, state, contamination) via CLIP,BLIP and LLMs
- Weight estimation using heuristics
- Final report generation with LLM synthesis
- Explainability via Grad-CAM, Eigen-CAM, and token attribution

The project is publicly hosted to demonstrate the value of academic innovation through the **GitHub Education for Students** program.

---

## Pipeline Overview

### 1. **Object Detection (YOLOv8)**
- Detects objects in the input image.
- Outputs: bounding boxes, class labels, confidence scores.

### 2. **Detection Evaluation**
- **Valid detection**: Known class + confidence ≥ 0.4
- **Uncertain detection**: "Unlabeled litter" or low-confidence

### 3. **Valid Detection Path**
- Heuristic prompt generation for material/state/contamination
- CLIP ranks image-text alignment; top scores selected

### 4. **Uncertain Detection Path**
- BLIP captioning + LLM material inference
- CLIP used for scoring multiple generated descriptions

### 5. **No Detection Fallback**
- Apply BLIP to whole image
- LLM suggests plausible materials and states
- CLIP ranks them

### 6. **Weight Estimation**
- Estimate volume based on class or bounding box
- Adjust for state (e.g., compacted)
- Compute final weight using material density

### 7. **Final Report Generation**
- LLM generates natural-language report summarizing:
  - Detected objects
  - Materials, states, contamination
  - Estimated weights
  - Uncertainties or remarks

---

## Explainable AI (XAI)

### Object Detection (YOLOv8)
- **Grad-CAM**: highlights localized class-based features
- **Eigen-CAM**: captures global activation context
- **Fusion**: combines both for clearer visual explanation

### CLIP Attribution
- **Token Attribution by Similarity Drop**:
  - Perturbs key words (e.g., "glass", "bottle")
  - Measures change in similarity score
  - Reveals word importance in predictions

---

## Technologies Used

- Python 3.10+
- YOLOv8 (Ultralytics)
- CLIP (OpenAI)
- BLIP (Salesforce)
- LLM (Phi-2 or similar)
- TorchCAM, Eigen-CAM
- OpenCV, Matplotlib, NumPy

---

## GitHub Topics

`YOLOv8` • `object-detection` • `CLIP` • `BLIP` • `LLM` • `XAI` • `waste-detection` • `environmental-AI` • `vision-language-models` • `Esprit-School-of-Engineering` • `GitHub-Education`

---

## 🙌 Acknowledgments

This project was completed at **Esprit School of Engineering** and hosted publicly as part of the GitHub Education for Students program to enhance institutional visibility and promote applied AI research.
