---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Identifiable Mixtures of Sparse Variational Gaussian Process Experts"
authors: ["Aidan Scannell", "Carl Henrik Ek", "Arthur Richards"]
date: 2021-05-26T10:48:12+01:00
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: 2021-05-26T10:48:12+01:00

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["3"]

# Publication name and optional abbreviated publication name.
publication: "UK Robotics and Autonomous Systems CDT Conference 2021"
publication_short: "UK RAS CDT Conference"

abstract: "Mixture models are inherently unidentifiable as different combinations of component distributions and mixture weights can generate the same distributions over the observations. We propose a scalable Mixture of Experts model where both the experts and gating functions are modelled using Gaussian processes. Importantly, this balanced treatment of the experts and the gating network introduces an interplay between the different parts of the model. This can be used to constrain the set of admissible functions reducing the identifiability issues normally associated with mixture models. The model resembles the original Mixture of Gaussian Process Experts method with a GP-based gating network. However, we derive a variational inference scheme that allows for stochastic updates enabling the model to be used in a more scalable fashion."

# Summary. An optional shortened abstract.
summary: ""

tags: ["gaussian-processes", "probabilistic-modelling", "variational-inference", "machine-learning", "python", "GPflow", "TensorFlow", "Bayesian-inference"]
tags: []
categories: []
featured: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter

url_pdf: publication/identifiable-mixtures-of-sparse-variational-gaussian-process-experts/oxford-2021-mogpe.pdf
url_code: "https://github.com/aidanscannell/mogpe"
url_dataset:
url_poster:
url_project: "https://www.aidanscannell.com/project/mixtures-of-sparse-variational-gaussian-process-experts/"
url_slides:
url_source:
url_video:

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects: ["mixtures-of-sparse-variational-gaussian-process-experts"]

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: ""
---
