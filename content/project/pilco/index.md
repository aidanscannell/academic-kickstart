---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Model-Based Reinforcement Learning with Gaussian Processes"
summary: "In this work I re-implemented the PILCO algorithm in python using Tensorflow and GPflow. This work was mainly carried out for personal development and some of the implementation is based on this [Python implementation](https://github.com/nrontsis/PILCO). This repository will mainly serve as a baseline for my future research."
authors: []
tags: ["gaussian-processes", "machine-learning", "python", "reinforcement-learning"]
categories: []
date: 2019-03-13

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

url_code: "https://github.com/aidanscannell/pilco-tensorflow"
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---
In this work I reimplemented the PILCO algorithm (originally written in MATLAB) in Python using Tensorflow and GPflow. 
This work was mainly carried out for personal development and some of the implementation is based on this [Python implementation](https://github.com/nrontsis/PILCO). 
This repository will mainly serve as a baseline for my future research.

I implemented the cart pole benchmark using MuJoCo and OpenAI. 
I did this because OpenAI's CartPole environment does not have a continuous action space and because the InvertedPendulum-v2 environment uses an "inverted" cart pole. 
The new environment represents the traditional cart pole benchmark with a continuous action space.

The env/cart_pole_env.py file contains the new CartPole class, based on InvertedPendulum-v2.
I also created the env/cart_pole.xml file defining the MuJoCo environment for the traditional cart pole.
