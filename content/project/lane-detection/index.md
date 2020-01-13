---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Autonomous Vehicle Lane Detection Software"
summary: "An application was designed following the model-view-controller architecture to enable multiple autonomous vehicle algorithms to be simulated in different views and to allow the input parameters to be altered in run time e.g. adaptive threshold parameters, coordinates for inverse perspective mapping, number of sample points etc. The code will run slower due to the MVC architecture."
authors: ["Aidan Scannell"]
tags: ["c++", "computer-vision", "robotics"]
categories: []
date: 2017-01-07

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

url_code: "https://github.com/aidanscannell/lane-detection"
url_video: "Lane_Detection.mp4"
url_pdf: ""
url_slides: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---
I undertook this project to strengthen my C++ and to gain a deeper understanding of the difficulties
of implementing autonomous capabilities. An application was designed following
the model-view-controller architecture to enable multiple autonomous vehicle algorithms to be simulated
in different
views and to allow the input parameters to be altered in run time e.g. adaptive threshold parameters,
coordinates for inverse perspective mapping, number of sample points etc. The code will run slower due
to the
MVC architecture.

### Lane Detection

The lane detection algorithm utilises image enhancement
techniques including temporal blurring and inverse
perspective mapping before splitting the image into two halves for further processing. Instances of the
**LaneDetector** class are then created for each image in order to detect the lane markers.
An adaptive threshold is then used to detect the edges within each image.
The **LineFinder** class is then used to detect lines using both the Hough Transform and
Probabilistic Hough Transform.
Any lines which do not resemble lane markers are removed (incorrect orientation etc).
A bitwise AND operation of the two results is then used to combine the results for optimal line
selection.
The Hough Transform function within the **LineFinder** class is then used to detect the 10 most
probable lines
within the resulting image.

The image is then sampled along it’s height and linear least squares
regression is used to calculate the best fit line for the lane marker.
The lines rho (distance from the coordinate origin) and theta (the line rotation angle in radians) are
then calculated.

Two instances of the **LaneTracker** class are then created
in order to track the lane marker in each image.
The line parameters (rho, theta) are used as inputs to the Kalman Filter.
If no best fit line is detected then the Kalman Filter predicts the parameters.

### Vehicle Detection

The vehicle detection algorithm utilises a Haar Cascade which
is trained using an MIT vehicle dataset.
The input frame is converted to grayscale before undergoing histogram equalisation.
Objects of different sizes are then detected using the Haar Cascade and stored in a list of rectangles.
The detected cars are then marked on the output image.
