---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Trajectory Optimisation in Learned Multimodal Dynamical Systems via Latent-ODE Collocation"
event: "2021 IEEE International Conference on Robotics and Automation"
event_url: "https://www.ieee-icra.org/index.aspx"
location: "Xi'an, China"
address:
  street:
  city:
  region:
  postcode:
  country:
summary: "In this talk I will present our ICRA 2021 paper \"Trajectory Optimisation in Learned Multimodal Dynamical Systems via Latent-ODE Collocation\"."
abstract: "This paper presents a two-stage method to perform trajectory optimisation in multimodal dynamical systems with unknown nonlinear stochastic transition dynamics. The method finds trajectories that remain in a preferred dynamics mode where possible and in regions of the transition dynamics model that have been observed and can be predicted confidently. The first stage leverages a Mixture of Gaussian Process Experts method to learn a predictive dynamics model from historical data. Importantly, this model learns a gating function that indicates the probability of being in a particular dynamics mode at a given state location. This gating function acts as a coordinate map for a latent Riemannian manifold on which shortest trajectories are solutions to our trajectory optimisation problem. Based on this intuition, the second stage formulates a geometric cost function, which it then implicitly minimises  by projecting the trajectory optimisation onto the second-order geodesic ODE; a classic result of Riemannian geometry. A set of collocation constraints are derived that ensure trajectories are solutions to this ODE, implicitly solving the trajectory optimisation problem."

# Talk start and end times.
#   End time can optionally be hidden by prefixing the line with `#`.
# date: 2021-05-20T21:20:33+01:00
date: 2021-06-03T11:00:00+01:00
date_end: 2021-06-03T11:30:00+01:00
all_day: false

# Schedule page publish date (NOT talk date).
publishDate: 2021-05-20T21:20:33+01:00

authors: ["Aidan Scannell"]
tags: ["control", "geometry", "machine-learning", "python", "JAX", "gaussian-processes", "probabilistic-modelling"]

# Is this a featured talk? (true/false)
featured: false

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

# Optional filename of your slides within your talk's folder or a URL.
url_slides:

url_code: "https://github.com/aidanscannell/trajectory-optimisation-in-learned-multimodal-dynamical-systems.git"
url_pdf:
url_video:

# Markdown Slides (optional).
#   Associate this talk with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: ["trajectory-optimisation-in-learned-multimodal-dynamical-systems"]
---
