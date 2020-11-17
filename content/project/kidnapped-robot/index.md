---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Kidnapped Robot"
summary: "This project involved developing algorithms capable of localising a robot within a known environment but at an unknown position and moving it to a target location. This was achieved in simulation using the BotSim library in Matlab and then implemented onto a real robot."
authors: ["Aidan Scannell"]
tags: ["ai", "matlab", "robotics"]
categories: []
date: 2016-12-29

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

url_pdf: "Kidnapped-Robot.pdf"
url_code: "https://github.com/aidanscannell/kidnapped-robot"
url_slides: ""
url_video: "kidnapped_robot2.mp4"

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---
This project involved developing algorithms capable of localising a robot within a known
environment but at an unknown position and moving it to a target location. This was
achieved in simulation using the BotSim library in Matlab and then implemented onto
a real robot.

The robot was limited to using a single ultrasound sensor, an odometry sensor and
two motors. The robot was designed and built to represent the simulated robot as
accurately as possible. This was achieved by positioning the ultrasound sensor
directly above the turning centre, located in the middle of the two motors. In
theory this configuration enabled the robot to turn without displacing the sensor,
although in reality this is unlikely.

The localisation algorithm utilised a particle filter to approximately calculate
the robots position. The Euclidean distance was used to score the particles with
a low variance resampling procedure. Once a suitable estimation for the position
of the robot was calculated, a wave-front based route planner was implemented to
generate a discretised route to the target. To ensure that the robot did not clash
with a wall, a smaller, inwardly offset map was generated and used in the route
planning. The motion of the robot was divided into rotation and translation,
therefore requiring separate turn and move commands. The list of unit moves from
the route planner was then combined into turn and forward commands for the robot.
The simulated robot performed scans and relocalised along the route to ensure its
accuracy as it moved.
