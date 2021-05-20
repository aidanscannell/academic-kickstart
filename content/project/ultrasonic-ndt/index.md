---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Ultrasonic Non-Destructive Testing"
summary: "This project entailed the design of an ultrasonic phased array for operation into the human body using Matlab."
authors: ["Aidan Scannell"]
tags: ["matlab"]
categories: []
date: 2016-12-29

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

url_pdf: "project/ultrasonic-ndt/Ultrasnic-NDT.pdf"
url_code: "https://github.com/aidanscannell/ultrasonic-non-destructive-testing-array-design"
url_video: "NDT.mp4"
url_slides: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---
This project entailed the design of an ultrasonic phased array for operation into the human body using Matlab. The testing
medium consisted of 10 points requiring inspection and a back wall 20 mm away in the z direction.
Huygen’s principle was used to generate a calibration array that enabled appropriate parameters to be selected and
used for the array simulation. The time domain data was converted to the frequency domain using Fourier transform
in order to simplify the analysis. The time domain signals were then simulated and used in three post-processing
algorithms (Total Focusing Method, Focused B-Scan and Linear B-Scan). The resulting data was analysed using
an Array Performance Indicator algorithm that offered a comparison of the different post-processing algorithms.
