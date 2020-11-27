---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

draft: true
title: "Handling Uncertainties in Learnt Probabilistic Transition Dynamics Models"
event: "FARSCOPE Seminar Series"
event_url:
location:
address:
  street:
  city:
  region:
  postcode:
  country:
summary:
abstract:

# Talk start and end times.
#   End time can optionally be hidden by prefixing the line with `#`.
date: 2020-03-05T15:00:00Z
date_end: 2020-03-05T16:00:00Z
all_day: false

# Schedule page publish date (NOT talk date).
publishDate: 2020-02-05T15:14:00Z

authors: ['Aidan Scannell']
tags: []

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
url_slides: /talks/farscope_seminar/farscope_seminar_03_20.html

url_code:
url_pdf:
url_video:

# Markdown Slides (optional).
#   Associate this talk with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: 

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---

In this talk I provide an overview of the work conducted in my PhD thus far.
I start by covering the uncertainties that arise when learning models from data and then present a short introduction into the Bayesian methodology; a principled framework for handling such uncertainties.
The work I present considers bimodal systems,
\begin{equation}\label{eq:modes}
\DeclareMathOperator{\E}{\mathbb{E}}
\DeclareMathOperator{\R}{\mathbb{R}}
  \mathbf{y} = \begin{cases}
    f^{(1)}(\mathbf{x}) + \epsilon\_1,\newline
    f^{(2)}(\mathbf{x}) + \epsilon\_2 \newline
  \end{cases}
\end{equation}
where $\epsilon\_i \sim \mathcal{N}(0, \Sigma\_{i})$ and $\epsilon\_1 \gg \epsilon\_2$
i.e. the noise in one mode is much larger relative to the other. 
The probabilistic model I introduce assumes that two latent functions $\mathbf{F} = {f^{(1)}, f^{(2)}}$ have generated $N$ pairs of
observations subject to additive i.i.d. Gaussian noise from one of two modes, resulting in
the data set $\mathcal{D} = \{(\mathbf{x}\_n, \mathbf{y}_n)\}\_{n=1}^N $. The
assignment of the $n^{\text{th}}$ data point is specified by the random (Bernoulli) variable
$\alpha_n \in \{0, 1 \}$. The model assumes that a Riemannian manifold
$h$ (which we parameterise as a Gaussian processs) separates the two modes.
As such, $h$ provides information regarding the structure of the aleatoric uncertainty present in the system.

I then present how we can project a trajectory optimisation problem onto the latent probabilistic manifolds learnt by our model.
The method provides a principled approach for uncertainty aware trajectory optimisation that can consider both epistemic and aleatoric
uncertainties to different degrees.
