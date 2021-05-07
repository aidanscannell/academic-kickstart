---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "GPJax - Gaussian Processes in Jax"
summary: ""
authors: []
tags: []
categories: []
date: 2021-05-06T14:35:24+01:00

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

url_code: "https://github.com/aidanscannell/GPJax"
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
I am developing a minimal Python package for implementing Gaussian process models in Python using JAX. I have spent a lot of time using GPflow and I like how they implement their GP library, in particular, their focus on variational inference and how they implement GP conditionals. As such, this package takes a similar approach but offers the benefits (and ease) of having JAX under the hood.

GPJax keeps in the spirit of JAX (to provide an extensible system for composable function transformations) by implementing its features as pure functions. However, managing the parameters associated with the different components in Gaussian process methods (compositions of mean functions, kernels, variational parameters etc) makes a purely functional approach less appealing. I have experimented using both haiku and objax for state management and neither of them provided a level of abstraction I was happy with. As a result, I now implement a simple approach to state management.

This package is a work in progress and functionality will be implemented when I need it for my research. If you like what I’m doing or have any recommendations then please reach out, or even better, get involved!
