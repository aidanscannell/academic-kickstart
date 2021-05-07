---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Trajectory Optimisation in Learned Multimodal Dynamical Systems via Latent-ODE Collocation"
authors: ["Aidan Scannell", "Carl Henrik Ek", "Arthur Richards"]
date: 2021-03-22T10:57:17Z
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: 2021-03-22T10:57:17Z

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["1"]

# Publication name and optional abbreviated publication name.
publication: "IEEE International Conference on Robotics and Automation"
publication_short: "ICRA"

abstract: "This paper presents a two-stage method to perform trajectory optimisation in multimodal dynamical systems with unknown nonlinear stochastic transition dynamics. The method finds trajectories that remain in a preferred dynamics mode where possible and in regions of the transition dynamics model that have been observed and can be predicted confidently. The first stage leverages a Mixture of Gaussian Process Experts method to learn a predictive dynamics model from historical data. Importantly, this model learns a gating function that indicates the probability of being in a particular dynamics mode at a given state location. This gating function acts as a coordinate map for a latent Riemannian manifold on which shortest trajectories are solutions to our trajectory optimisation problem. Based on this intuition, the second stage formulates a geometric cost function, which it then implicitly minimises by projecting the trajectory optimisation onto the second-order geodesic ODE; a classic result of Riemannian geometry. A set of collocation constraints are derived that ensure trajectories are solutions to this ODE, implicitly solving the trajectory optimisation problem."

# Summary. An optional shortened abstract.
summary: "Synergising Bayesian inference and Riemannian geometry for control in multimodal dynamical systems."

tags: ["control", "geometry", "machine-learning", "python", "JAX", "gaussian-processes", "probabilistic-modelling"]
categories: []
featured: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter

url_pdf: "/publication/trajectory-optimisation-in-learned-multimodal-dynamical-systems-via-latent-ode-collocation/paper.pdf"
url_code: "https://github.com/aidanscannell/trajectory-optimisation-in-learned-multimodal-dynamical-systems"
url_dataset:
url_poster:
url_project:
url_slides:
url_source:
url_video: "/publication/trajectory-optimisation-in-learned-multimodal-dynamical-systems-via-latent-ode-collocation/icra-2021-traj-opt.mp4"

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
projects: ["trajectory-optimisation-in-learned-multimodal-dynamical-systems"]

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: ""
---
