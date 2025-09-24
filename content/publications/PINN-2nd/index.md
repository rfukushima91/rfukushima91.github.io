---
title: "Physics-Informed Deep Learning for Estimating the Spatial Distribution of Frictional Parameters in Slow Slip Regions"

# Authors
authors:
  - admin
  - Masayuki Kano
  - Kazuro Hirahara
  - Makiko Ohtani
  - Kyungjae Im
  - Jean-Philippe Avouac

# Author notes (optional)
# author_notes:
#   - 'Equal contribution'

date: '2025-05-09T00:00:00Z'  # Placeholder date (replace with actual date)

# Schedule page publish date (NOT publication's date).
publishDate: '2025-05-09T00:00:00Z'  # Placeholder date (replace with actual publish date)

# Publication type.
publication_types: ['article-journal']

# Publication name and optional abbreviated publication name.
publication: "*Journal of Geophysical Research: Solid Earth*"
publication_short: "*JGR: Solid Earth*"

abstract: 'Slow slip events (SSEs) have been observed in many subduction zones and are understood to result from frictional unstable slip on the plate interface. The diversity of their characteristics and the fact that interplate slip can also be seismic suggest that frictional properties are heterogeneous. We are however lacking methods to determine spatial variations of frictional properties. In this paper, we employ a Physics-Informed Neural Network (PINN) to achieve this goal using a synthetic model inspired by the long-term SSEs observed in the Bungo channel. PINN is a deep learning technique that can be used to solve the differential equations representing the physics of the problem and determine the model parameters from observations. We start with an idealized case where it is assumed that fault slip is directly observed. We next move to a more realistic case where the observations consist of synthetic surface displacement velocity data measured by virtual GNSS stations. We find that the geometry and friction properties of the velocity weakening region, where the slip instability develops, are well estimated, especially if surface displacement velocity above the velocity weakening region is observed. Our PINN-based method can be seen as an inversion technique with the regularization constraint that fault slip obeys a particular friction law. This approach remediates the issue that standard regularization techniques are based on non-physical constraints. Our results show that the PINN-based method is a promising approach for estimating the spatial distribution of friction parameters from GNSS observations.'

# Summary. An optional shortened abstract.
summary: ''

tags:
  - Deep Learning
  - Geophysics
  - Slow Slip Events
  - Physics-Informed Neural Networks

# Display this page in the Featured widget?
featured: true

# Standard identifiers for auto-linking
hugoblox:
  ids:
    doi: 10.1029/2024JB030256

# Custom links
# links:
#   - type: pdf
#     url: ""
#   - type: code
#     url: ""  # Placeholder (replace with actual URL if available)
#   - type: dataset
#     url: ""  # Placeholder (replace with actual URL if available)
#   - type: slides
#     url: ""  # Placeholder (replace with actual URL if available)
#   - type: source
#     url: ""  # Placeholder (replace with actual URL if available)
#   - type: video
#     url: ""  # Placeholder (replace with actual URL if available)

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
image:
  caption: ''
  focal_point: ''
  preview_only: false

# Associated Projects (optional).
projects: []

# Slides (optional).
slides: ""
---
