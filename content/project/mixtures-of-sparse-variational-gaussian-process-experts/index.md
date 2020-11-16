---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Identifiable Mixtures of Sparse Variational Gaussian Process Experts"
summary: "This work introduces a variational lower bound for the mixture of Gaussian process experts model with a GP based gating network based on sparse GPs. The model (and inference) are implemented in GPflow/TensorFlow."
authors: []
tags: ["gaussian-processes", "variational inference", "probabilistic-modelling", "machine-learning", "python", "gpflow", "tensorflow", "bayesian-inference"]
categories: []
date: 2020-11-16T19:31:03Z

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

url_code: "https://github.com/aidanscannell/mogpe"
url_pdf: ""
url_slides: ""
urlivideo: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---
This work derives a novel variational lower bound for the mixture of Gaussian process experts model with a GP based gating network based on sparse GPs. 
The model (and inference) are implemented as a package ([`mogpe`](https://github.com/aidanscannell/mogpe)) written
in [GPflow](https://github.com/GPflow/GPflow)/[TensorFlow](https://github.com/tensorflow/tensorflow).

Mixture models are inherently unidentifiable as different combinations of component distributions
and mixture weights can generate the same distributions over the observations.
This work proposes a scalable mixture of experts model where both the experts and gating functions are
modelled using Gaussian processes.
Importantly, this balanced treatment of the experts and the gating network introduces an
interplay between the different parts of the model.
This can be used to constrain the set of admissible
functions reducing the identifiability issues normally associated with mixture models.
This work derives a variational lower bound that allows for stochastic updates enabling the model to
be used in a scalable fashion.



