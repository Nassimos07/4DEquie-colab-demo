<div align="center">
  <img src="data/github-files/github-banner.svg" alt="4DEquie Colab Demo Banner" width="100%" />
</div>

<div align="center">

[![Platform](https://img.shields.io/badge/Platform-Google%20Colab-F9AB00.svg)](https://colab.research.google.com/drive/1yu7MEK9-bvO8iBZ1GZ9QbAJ_-V3_uHeA?usp=sharing)
[![Notebook](https://img.shields.io/badge/Notebook-Ready-success.svg)](https://colab.research.google.com/drive/1yu7MEK9-bvO8iBZ1GZ9QbAJ_-V3_uHeA?usp=sharing)
[![Usage](https://img.shields.io/badge/Usage-Demo%20%26%20Guide-blue.svg)](https://colab.research.google.com/drive/1yu7MEK9-bvO8iBZ1GZ9QbAJ_-V3_uHeA?usp=sharing)
[![Status](https://img.shields.io/badge/Status-Active-success.svg)](#-features)

</div>

<div align="center">
<span style="color:#1E90FF;"><strong>4DEquie Colab Demo</strong></span> — a lightweight repository that points users directly to the Google Colab workflow.
</div>
<div align="center">
This repo is a demo and usage guide, not a full MLOps project or training repository.
</div>
<div align="center">
Users can open the notebook, follow the Colab steps, and run 4DEquie without local setup.
</div>

---

## ✦ <span style="color:#1E90FF;">Pipeline</span>

<div align="center">Open Colab Notebook → Follow Notebook Steps → Run 4DEquie in Colab → Review Outputs</div>

- **Entry point**: Google Colab notebook
- **Execution**: fully notebook-based workflow
- **Environment**: Google Colab
- **Goal**: help users run 4DEquie smoothly with minimal friction

## ✦ <span style="color:#1E90FF;">Features</span>

- Simple repository focused on user onboarding
- Direct access to the official Google Colab notebook
- No local installation flow to maintain
- No training pipeline, package structure, or dependency management overhead
- Suitable as a public-facing demo or quick-start guide

## ✦ <span style="color:#1E90FF;">How 4DEquine Works</span>

4DEquine reconstructs a full 4D horse model from a monocular video.
In practice, that means recovering the horse shape in 3D and tracking its motion over time.
The final result is an animatable 3D representation that stays consistent across frames.

### ◐ Step 1, Segment the horse

- **SAM 3** identifies the horse in the first frame
- This gives the pipeline a clean starting region for the target animal
- The goal is to isolate the horse from the background before temporal tracking begins

### ◐ Step 2, Track the horse through the video

- **SAMURAI** tracks the horse across the full sequence
- This keeps the subject localized from frame to frame
- Stable tracking is important because later stages depend on temporal consistency

### ◐ Step 3, Estimate 2D keypoints

- **ViTPose++** predicts 2D animal joint locations in image space
- These keypoints describe the visible pose of the horse in each frame
- At this stage, the result is still 2D, not full 3D motion yet

### ◐ Step 4, Lift the motion into 3D

- **AniMoFormer** lifts the 2D keypoints into a full 3D pose sequence
- It uses **VAREN**, a parametric horse model built from real 3D scans
- You can think of VAREN as a horse-specific equivalent of SMPL for humans
- This stage recovers articulated structure, pose, and temporal motion in 3D

### ◐ Step 5, Build the final 4D avatar

- **EquineGS** reconstructs a renderable 3D Gaussian Splatting avatar
- The output can be visualized from new viewpoints
- The sequence remains temporally coherent, so the horse motion is preserved over time

### ◐ Final output

- a full 3D horse representation tracked across the video
- articulated pose over time
- mesh and geometry information that can be inspected frame by frame
- outputs that are useful for visualization, motion analysis, and downstream research workflows

## ✦ <span style="color:#1E90FF;">Setup</span>

### ◐ Dependencies

No local dependencies are required for this repository.
Users should run the workflow directly in Google Colab.

Open the notebook:

```bash
https://colab.research.google.com/drive/1yu7MEK9-bvO8iBZ1GZ9QbAJ_-V3_uHeA?usp=sharing
```

Additional parameters:
- none

### ◐ Data

- Data access and runtime steps are handled inside the Colab notebook
- This repository does not ship datasets, weights, or local assets
- Follow the notebook instructions for inputs and outputs

## ✦ <span style="color:#1E90FF;">Google Colab Notebook</span>

Open the notebook here:

- **Colab link**: https://colab.research.google.com/drive/1yu7MEK9-bvO8iBZ1GZ9QbAJ_-V3_uHeA?usp=sharing

You can also use the badge below:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1yu7MEK9-bvO8iBZ1GZ9QbAJ_-V3_uHeA?usp=sharing)

## ✦ <span style="color:#1E90FF;">Usage</span>

For this project, usage happens inside the notebook.

```bash
Open the Colab link and run the notebook cells step by step.
```

Additional parameters:
- use a Colab GPU runtime if the notebook recommends it
- follow the notebook order without skipping setup cells

## ✦ <span style="color:#1E90FF;">Project Structure</span>

```text
.
└── README.md
```

## ✦ <span style="color:#1E90FF;">Notes</span>

- This repository is intentionally minimal
- It is designed as a guide and demo entry point for end users
- If the Colab notebook changes, update the link here so users always land on the correct workflow

## ✦ <span style="color:#1E90FF;">License</span>

No license file is included yet.
Add one before wider public distribution.
