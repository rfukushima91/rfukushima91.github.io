---
# Leave the homepage title empty to use the site title
title: ''
date: 2022-10-24
type: landing

design:
  # Default section spacing
  # spacing: '1rem'

sections:
  - block: resume-biography
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
      text: ''
      # Show a call-to-action button under your biography? (optional)
      button:
        text: Download CV (last updated:Sep 2025)
        url: uploads/CV.pdf
      headings:
        about: ''
        education: ''
        interests: ''
      # Avatar customization
      avatar:
        size: medium # Options: small (150px), medium (200px, default), large (320px), xl (400px), xxl (500px)
        shape: circle # Options: circle (default), square, rounded
    design:
      spacing:
        padding: ['5px', '0', '10px', '0']
      #  # Apply a gradient background
      # css_class: hbx-bg-gradient
      background:
        image:
          filename: 

  # - block: markdown
  #   content:
  #     title: 'Project'
  #     subtitle: ''
  #     text: |-
  #       Coming soon ...
  #   design:
  #     columns: '1'
  #     spacing:
  #       padding: ['10px', '0', '10px', '0']
  
  - block: markdown
    content:
      title: 'News'
      subtitle: ''
      text: |-        
        <table style="border-collapse: collapse; width: 100%;">

          <tr>
            <th style="border: none; text-align: left;">2025</th>
            <th style="border: none; text-align: left;">  </th>
          </tr>
          <tr>
            <td style="border: none;">Sep</td>
            <td style="border: none;">I presented my research on adjoint-based dynamic rupture inversion with slip-weakening friction at the 2025 SCEC Annual Meeting. </td>
          </tr>
          <tr>
            <td style="border: none;">July</td>
            <td style="border: none;">I was invited as a spearker at Caltech GMG Deep Dive 2025: Optimization and Control. <br> My presentation title was "Adjoint-based and deep learning-based inversion for fault friction from geodetic and seismic observations".
          </tr>
          <tr>
            <td style="border: none;">May</td>
            <td style="border: none;">I joined JpGU 2025 and presented my research on PINN-based frictional property estimation for 2010 Bungo SSEs. <br>
            I won the Outstanding Student Presentation Awards! </td>
          </tr>

          <tr>
            <th style="border: none; text-align: left;">2024</th>
            <th style="border: none; text-align: left;">  </th>
          </tr>
          <tr>
            <td style="border: none;">Dec</td>
            <td style="border: none;">I presented my PINN-related work at AGU 2024. </td>
          </tr>
          <tr>
            <td style="border: none;">Sep</td>
            <td style="border: none;">I started my Ph.D. at Stanford! </td>
          </tr>
        </table>
    design:
      columns: '1'
      spacing:
        padding: ['10px', '0', '10px', '0'] 

  # - block: collection
  #   id: projects
  #   content:
  #     title: Projects
  #     filters:
  #       folders:
  #         - projects
  #       featured_only: false
  #   design:
  #     view: article-grid
  #     columns: 2
  #     spacing:
  #       padding: ['20px', '0', '10px', '0']  
 
 
# TO DO: add the publication page (?) #

  # - block: collection
  #   content:
  #     title: Featured Publications
  #     filters:
  #       folders:
  #         - publications
  #       featured_only: true
  #   design:
  #     view: article-grid
  #     columns: 2
  
  # - block: collection
  #   id: papers
  #   content:
  #     title: Publications
  #     text: ''
  #     filters:
  #       folders:
  #         - publications
  #       exclude_featured: false
  #   design:
  #     view: citation

  
  # - block: collection
  #   id: talks
  #   content:
  #     title: Recent & Upcoming Talks
  #     filters:
  #       folders:
  #         - events
  #   design:
  #     view:  card
  
  # - block: collection
  #   id: news
  #   content:
  #     title: Recent News
  #     subtitle: ''
  #     text: ''
  #     # Page type to display. E.g. post, talk, publication...
  #     page_type: blog
  #     # Choose how many pages you would like to display (0 = all pages)
  #     count: 5
  #     # Filter on criteria
  #     filters:
  #       author: ''
  #       category: ''
  #       tag: ''
  #       exclude_featured: false
  #       exclude_future: false
  #       exclude_past: false
  #       publication_type: ''
  #     # Choose how many pages you would like to offset by
  #     offset: 0
  #     # Page order: descending (desc) or ascending (asc) date.
  #     order: desc
  #   design:
  #     # Choose a layout view
  #     view: card
  #     # Reduce spacing
  #     spacing:
  #       padding: [0, 0, 0, 0]

  
  - block: cta-card
    demo: true # Only display this section in the Hugo Blox Builder demo site
    content:
      title: 👉 Build your own academic website like this
      text: |-
        This site is generated by Hugo Blox Builder - the FREE, Hugo-based open source website builder trusted by 250,000+ academics like you.

  #       <a class="github-button" href="https://github.com/HugoBlox/hugo-blox-builder" data-color-scheme="no-preference: light; light: light; dark: dark;" data-icon="octicon-star" data-size="large" data-show-count="true" aria-label="Star HugoBlox/hugo-blox-builder on GitHub">Star</a>

  #       Easily build anything with blocks - no-code required!

  #       From landing pages, second brains, and courses to academic resumés, conferences, and tech blogs.
  #     button:
  #       text: Get Started
  #       url: https://hugoblox.com/templates/
  #   design:
  #     card:
  #       # Card background color (CSS class)
  #       css_class: 'bg-primary-700'
  #       css_style: ''
---
