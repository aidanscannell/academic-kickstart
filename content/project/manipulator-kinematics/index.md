---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

draft: true
title: "Manipulator Kinematics and Trajectory Planning"
summary: "This project involved deriving and implementing the serial kinematics for a Lynxmotion arm as well as the parallel kinematics for a planar parallel robot used in surgical procedures."
authors: ["Aidan Scannell"]
tags: ["matlab", "robotics"]
categories: []
date: 2017-12-14

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter

url_pdf: "Manipulator-Kinematics.pdf"
url_code: "https://github.com/aidanscannell/manipulator-kinematics"
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---
This project involved deriving and implementing the serial kinematics for a Lynxmotion arm as well as the parallel kinematics for a planar parallel robot used in surgical procedures.

### Serial Manipulator
This involved deriving the DH representation of the forward kinematics for the Lnyxmotion arm before analysing the workspace of the centre of the wrist. I then derived the inverse kinematics model for the manipulator (analytical solution) and tested the model on a pick and place task.
[image]: serial_kinematics.png "Serial Kinematics"
Following this, I implemented several trajectory planning algorithms in both joint space and cartesian space, namely:

1. Free motion trajectory,
2. Straight line trajectory,
3. Cubic and quintic polynomial trajectories,
4. Linear with parabolic blends trajectory,
5. Obstacle avoidance trajectory.

### Parallel Manipulator
The figure below shows a needle positioning parallel robot that is used for surgical procedures. This is the parallel robot that was studied and implemented. 
[image]: parallel-manipulator.png "Parallel Manipulator"
