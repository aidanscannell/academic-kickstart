---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Probabilistic Modelling"
summary: "I am in the process of creating Jupyter notebooks for several probabilistic models (Bayesian linear regression, Gaussian process regression) and approximate inference algorithms. Particular focus has been put on providing detailed theory as well as easy to follow code."
authors: ["Aidan Scannell"]
tags: ["gaussian-processes", "machine-learning", "python"]
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

url_code: "https://github.com/aidanscannell/probabilistic-modelling"
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
I am in the process of creating Jupyter notebooks for several probabilistic models and approximate inference algorithms. Particular focus has been put on providing detailed theory as well as easy to follow code.

So far I have created notebooks for Bayesian linear regression and Gaussian process regression. These can be found on my [Github (probabilistic modelling)](https://github.com/aidanscannell/probabilistic-modelling).

### Bayesian linear regression
I start by introducing regression and formulating linear regression as a Bayesian model, before deriving
the parameters of the posterior distribution. The rest of the notebook then provides a well commented implementation of Bayesian
linear regression. 

### Gaussian process regression
I start by defining the squared exponential (SE) kernel so that we can formulate our Gaussian process (GP) prior and then visualise it by drawing samples from it. We then define an underlying function that we are trying to recover, a sine function $\mathbf{y} = sin(\mathbf{x})$. From this we then generate a noise free input-output training data set and then formulate the joint distribution between the training targets and the test targets. We then condition our joint Gaussian prior distribution on the observations, which leads to the key predictive equations for Gaussian process regression. We then provide a practical algorithm for implementing Gaussian process regression and visualise our posterior. Next, we extend the model do deal with noisy observations, that is, $\mathbf{y} = sin(\mathbf{x}) + \epsilon$, where $\epsilon \sim \mathcal{N}(0, \sigma\_n^2)$. Following this we apply Bayesian inference to Gaussian process regression in order to infer the hyper-parameters from the data, which provides automatic Ocam's razor. 
<!--Noise free-->
<!--Noisy observations -->
<!--Hyper-parameter optimisation -->

