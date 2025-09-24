---
title: 'Projects'
date: 2024-05-19
type: landing

design:
  # Section spacing
  spacing: '5rem'

# Page sections
sections:
  # - block: markdown
  #   content:
  #     title: 'Projects'
  #     subtitle: ''
  #     text: |-
  #       Coming soon ...
  #   design:
  #     columns: '1'

  - block: collection
    id: reserch
    content:
      title: Research
      filters:
        folders:
          - research
        featured_only: false
    design:
      view: article-grid
      show_date: false
      show_read_time: false
      show_read_more: true
      columns: 2
      spacing:
        padding: ['20px', '0', '10px', '0']  

  # - block: collection
  #   content:
  #     title: Projects
  #     text: I enjoy making things. Here are a selection of projects that I have worked on over the years.
  #     filters:
  #       folders:
  #         - projects
  #   design:
  #     view: article-grid
  #     fill_image: false
  #     columns: 3
  #     show_date: false
  #     show_read_time: false
  #     show_read_more: false
---
