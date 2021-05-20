---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "UAV Swarm"
summary: "This project involved developing distributed software enabling a swarm of fixed wing UAVs to track a pollutant cloud. A discrete time state space model of the world was produced and a finite state machine was used to add intelligence."
authors: ["Aidan Scannell"]
tags: ["ai", "matlab", "robotics"]
categories: []
date: 2016-11-10

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

url_pdf: "project/uav-swarm/UAV-Swarm-Simulation.pdf"
url_code: "https://github.com/aidanscannell/uav-swarm"
url_video: "UAV_Software_Simulation2.mp4"
url_slides: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

This project involved developing distributed
software enabling a swarm of fixed wing UAVs to track a pollutant
cloud. A discrete time state space model of the world was produced and a finite state
machine was used to add intelligence.
The UAV swarm is capable of locating any pollutant clouds in the area and tracking the 1
PPM concentration contour
while spreading out along the cloud to ensure that the complete perimeter is tracked.
The simulation is capable of using multiple agents to locate and track the clouds.
It uses several swarm behaviour features that reduce the number of collisions and
enables the swarm to spread around
the cloud.
