---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Amazon Picking Challenge"
summary: "As part of the FARSCOPE CDT program I worked in a team to develop a solution to Amazon’s picking challenge. This involved designing a robotic pick-and-place system that was capable of recognising and grasping both known and novel objects in cluttered environments."
authors: ["Aidan Scannell"]
tags: ["ai", "computer-vision", "machine-learning", "python", "robotics"]
categories: []
date: 2018-04-26

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

url_code: ""
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
As part of the FARSCOPE CDT program I worked in a team to develop a solution to Amazon’s picking challenge. This involved designing a robotic pick-and-place system that was capable of recognising and grasping both known and novel objects in cluttered environments.

### Background of The Amazon Picking Challenge

Amazon.com is able to quickly package and ship millions of items to customers from a network of fulfilment centers all over the globe. This wouldn&#39;t be possible without leveraging cutting-edge advances in technology. Amazon&#39;s automated warehouses are successful at efficiently moving goods within a warehouse. However, commercially viable automated picking in unstructured environments still remains a difficult challenge.

The 2016 Amazon Picking Challenge (the “Challenge”) is a skill challenge sponsored by Amazon Robotics LLC (the “Sponsor”) aimed to strengthen the ties between the industrial and academic robotic communities and promote shared and open solutions to some of the big problems in unstructured automation. The Challenge will task entrants with building their own robot hardware and software (collectively, a “Robot”) that can attempt simplified versions of the general task of picking items from shelves. Selected finalists will have their Robots presented with a stationary and lightly populated inventory shelf and be asked to pick a subset of the products from the shelf and put them in a tote and also stow products into the shelf. The Challenge combines object recognition, pose recognition, grasp planning, compliant manipulation, motion planning, task planning, task execution, and error detection and recovery. 

### Object Detection

In this project I was tasked with the object detection and it’s integration with other subsystems.

I trained a Faster-RCNN (Region-based Convolutional Neural Network) using <a href="https://github.com/tensorflow/models/tree/master/research/object%5C_detection">Tensorflow&#39;s Object Detection API</a> and this <a href="http://rll.berkeley.edu/amazon_picking_challenge/">dataset</a> from Berkeley. R-CNN, or Region-based Convolutional Neural Network, consist of 3 simple steps:


1. Scan the input image for possible objects using an algorithm called Selective Search, generating say ~1000 region proposals,
2. Run a convolutional neural net (CNN) on top of each of these region proposals,
3. Take the output of each CNN and feed it into a) an SVM to classify the region and b) a linear regressor to tighten the bounding box of the object, if such an object exists.

So, on high level, we first propose regions, then extract features, and then classify those regions based on their features. R-CNN is very intuitive, but very slow. So, Faster R-CNN resembled the original R-CNN in many ways, but improved on its detection speed through two main augmentations:

1. Performing feature extraction over the image before proposing regions, thus only running one CNN over the entire image instead of 1000 CNN’s over 1000 overlapping regions,
2. Replacing the SVM with a softmax layer, thus extending the neural network for predictions instead of creating a new model.

For more details on Faster-RCNN please refer to the original [paper](https://arxiv.org/pdf/1506.01497.pdf).
