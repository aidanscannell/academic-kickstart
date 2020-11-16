---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Trajectory Optimisation in Learned Multimodal Dynamical Systems"
summary: ""
authors: []
tags: ["optimal-control", "gaussian-processes", "variational inference", "probabilistic-modelling", "machine-learning", "python", "JAX"]
categories: []
date: 2020-11-16T21:29:53Z

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

url_code: "https://github.com/aidanscannell/trajectory-optimisation-on-probabilistic-manifolds-jax"
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

This work presents a two-stage method to
perform trajectory optimisation in multimodal dynamical systems with unknown nonlinear stochastic
transition dynamics.
The method finds trajectories that remain in a preferred dynamics mode
where possible and in regions of the transition dynamics model that
have been observed and can be predicted confidently.

The first stage leverages a mixture of Gaussian process experts method
([`mogpe`](https://github.com/aidanscannell/mogpe)) written
in [GPflow](https://github.com/GPflow/GPflow)/[TensorFlow](https://github.com/tensorflow/tensorflow)
to learn a predictive dynamics model from historical data.
Importantly, this model learns a gating function that indicates the probability of being in a particular
dynamics mode at a given state location.
In the second stage,
this gating function acts as a coordinate map for a latent Riemannian manifold on which
geodesics are solutions to our trajectory optimisation problem.
Geodesics on this manifold satisfy a continuous-time second-order ODE.
A set of collocation constraints are derived that ensure trajectories are solutions to this ODE,
implicitly solving the trajectory optimisation problem.
The trajectory optimisation is implemented in [JAX](https://github.com/google/jax).
