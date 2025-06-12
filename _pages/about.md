---
layout: about
title: about
permalink: /
# subtitle: <a href='#'>Affiliations</a>. Address. Contacts. Motto. Etc.

# profile:
#   align: right
#   image: prof_pic.jpg
#   image_circular: false # crops the image to make it circular
#   more_info: >
#     <p>555 your office number</p>
#     <p>123 your address street</p>
#     <p>Your City, State 12345</p>

news: true # includes a list of news items
selected_papers: true # includes a list of papers marked as "selected={true}"
social: true # includes social icons at the bottom of the page
---

# DiffSPH

{% include figure.liquid path="assets/img/diffSPH.png" title="example image" class="img-fluid rounded z-depth-1" %}

Our fully differentiable SPH solver that can do it all just got its first public beta release!

Included in doing it all is:
- δ-SPH and δ+-SPH for weakly compressible simulations
- IISPH and DFSPH for incompressible simulations
- CompSPH, CRKSPH, PESPH and the classic Monaghan scheme for compressible simulations
- mDBC boundary conditions for rigid bodies
- Inlets and Oulets with buffer zones
- Periodic BCs using minimum image conventions
- Neumann and Dirichlet BCs
- grad-H, kernel renormalization and CRK correction schemes
- δ+ and implicit particle shifting
- Monaghan and Owen schemes for adaptive particle support radii
- Balsara, Morris, Rosswog, Cullen Dehnen artificial viscosity switches
- Sub particle scale turbulence modelling
- Differentiable generation of initial conditions using SDFs
- Hierarchical and compact hashing based neighbor searching
- Verlet lists for neighborhood searches
- Most Common SPH Kernel Functions (Wendland, B-Spline, Poly6) used across the fields

You can also:
- Solve inverse problems
- Use loss based physics
- Parameter estimation
- Shape optimization
- Closure Modelling
- ... and much more

<!-- Write your biography here. Tell the world about yourself. Link to your favorite [subreddit](http://reddit.com). You can put a picture in, too. The code is already in, just name your picture `prof_pic.jpg` and put it in the `img/` folder.

Put your address / P.O. box / other info right below your picture. You can also disable any of these elements by editing `profile` property of the YAML header of your `_pages/about.md`. Edit `_bibliography/papers.bib` and Jekyll will render your [publications page](/al-folio/publications/) automatically.

Link to your social media connections, too. This theme is set up to use [Font Awesome icons](https://fontawesome.com/) and [Academicons](https://jpswalsh.github.io/academicons/), like the ones below. Add your Facebook, Twitter, LinkedIn, Google Scholar, or just disable all of them. -->
