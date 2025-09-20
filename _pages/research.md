---
layout: page
permalink: /research/
title: research statement
description: This statement is from mid september 2025, things may have changed.
nav: true
nav_order: 6
---
# Research Statement 

## I. Introduction

A central challenge in modern science and engineering is the development of predictive, tractable, and scalable simulations for complex physical systems. My research agenda targets this challenge by creating novel methods to solve demanding inverse problems, with applications ranging from optimizing aerodynamic shapes for energy efficiency to modeling the complex fluid-structure interactions of offshore wind turbines. My research builds upon a career trajectory that began in computer graphics, focused on efficiency and adaptability using Smoothed Particle Hydrodynamics (SPH), and has evolved into a computational fluid dynamics (CFD) direction. My postdoctoral work has centered on creating differentiable SPH solvers and novel Graph Neural Network architectures to enable this new class of problem-solving, and this statement outlines my contributions and future agenda to develop a predictive framework that combines traditional numerical approaches with learned closure models for scalable and grounded solutions to complex multi-physics problems.

## II. Past and Present

### A. Doctoral Research: Spatially Adaptive SPH

**The Problem:** At the outset of my PhD, the primary bottleneck for large-scale SPH in both computer graphics and scientific computing was computational cost. Simulating fluids with uniform high resolution is inefficient, as fine-scale details are often localized to specific regions like free surfaces and near-boundary layers. The central challenge was to develop a spatially adaptive simulation scheme that focuses computational effort where most needed, while remaining robust and performant on modern GPU architectures, even for challenging incompressible fluid scenarios.

**Approach & Methods:** I developed novel numerical methods, including a semi-analytic technique for multi-scale consistent boundary handling, and introduced new algorithmic strategies, such as using genetic algorithms for optimizing particle refinement. These innovations were integrated into openMaelstrom, an open-source framework I created. Designed with a computer scientist's perspective, it features domain-specific languages for expandability and highly optimized data handling. The result was a framework for highly adaptive simulations that improved upon existing methods by orders of magnitude, and which is still being used actively.

**Key Findings & Significance:** Crucially, this work presaged my current research focus. To optimize spatial adaptivity, I developed a strategy that utilized a differentiable error term—a technique conceptually parallel to the loss-driven optimization in modern differentiable physics. This insight, combined with hybrid numerical-analytic methods, yielded exceptionally performant simulation tools. This also built the foundation for my subsequent work, providing efficient and robust forward solvers and algorithms that were augmented by differentiable approaches and used for data-driven machine learning models.

**Outcomes:** This work produced four top-tier publications in computer graphics (three in ACM TOG, one in CGF), and additional peer-reviewed conference and journal articles. The initial work on adaptive SPH formed the basis of a successful DFG Individual Grant (KO 2960/15-1), which I co-authored. This grant funded my own research and that of another PhD student, demonstrating the broader impact and recognition of this work.

### B. Postdoctoral Research: GNNs & Differentiable Physics

My PhD solvers, while efficient for forward problems, were ill-suited for inverse problems, motivating two questions: Can we build differentiability directly into the solver, and can we use machine learning to replace heuristics with learned solutions? This required a pivot from building strictly forward solvers to creating differentiable frameworks and novel machine learning models for physics that are well suited to unstructured Lagrangian problems.

**New Skills & Area:** This pivot demanded a significant expansion of my skillset into machine learning and differentiable programming. I developed deep expertise in Graph Neural Networks, which are a natural fit for particle-based simulations. Notably, my move to TUM enabled me to connect with the CFD community, allowing me to expand my knowledge of numerical methods with the validation-first perspective essential for quantitative science.

**Contributions & Outcomes:** My postdoctoral research has yielded two distinct, yet synergistic, outcomes:

1. **A General-Purpose Differentiable SPH Framework:** My primary contribution is diffSPH, the spiritual and technical successor to openMaelstrom. It incorporates the performance insights from my PhD while dramatically expanding the scope beyond incompressible fluids to weakly-compressible and compressible shock-capturing problems. This framework enables the direct, gradient-based solution of inverse problems like shape optimization and parameter estimation. This work, co-authored with my supervisor Prof. Nils Thuerey, culminated in a manuscript currently under review at the Journal of Computational Physics (JCP).

2. **Fundamental Advances in SPH Boundary Handling:** In parallel, I continued to advance the core numerics of SPH. Building directly on my dissertation’s semi-analytic method, I developed a fully analytic boundary handling approach that provides exact, algebraic solutions to an arbitrary order of accuracy. This method has significant potential beyond SPH, as it provides a rigorous mathematical framework for coupling particle-based methods with mesh-based methods (FEM), a long-standing challenge in computational engineering. This second manuscript, enabled by my pivot into a CFD mindset, is also under review at JCP.

**Synthesis:** Together, these contributions demonstrate my ability to conduct research at both the cutting edge of machine learning for physics and at the foundational level of numerical methods, a duality further highlighted by my publication in ICLR 2024\. My current work now focuses on synthesizing these threads: using the diffSPH framework to learn closure models and correctors for CFD, as well as scaling to large-scale problems using Transformers. The promise of this direction has already sparked active discussions and planned collaborations with leading researchers in the field, forming the basis of my future research agenda.

## III. The Future

### A. Project 1: Closure Modelling with Differentiable Physics

**Research Question:** One of the most significant and long-standing challenges in CFD is turbulence closure modeling, particularly for Large Eddy Simulations (LES). Traditional models rely on heuristics and simplifying assumptions that limit their accuracy in complex, real-world flows. Can we leverage differentiable physics and modern neural network architectures to learn more accurate and robust sub-particle scale (SPS) closure models directly from high-fidelity data?

**Methodology & Feasibility:** My postdoctoral work has already built the essential tools for this project. The diffSPH framework provides the differentiable solver, and my work on GNNs provides the architectural foundation.I will develop a hybrid "solver-in-the-loop" framework where a Graph Transformer, an architecture well-suited for capturing long-range dependencies in turbulent flows, is trained to predict the non-resolved SPS stresses. By embedding this GNN within the differentiable SPH solver, we can train the entire system end-to-end by minimizing the error against high-resolution simulation data or analytical results. This hybrid approach is key to ensuring stability and generalization; the trusted numerical solver handles the resolved scales, while the learned model is responsible only for the closure term, a task for which machine learning is exceptionally well-suited.

**Expected Outcomes & Impact:** This project will result in a novel, GNN-based closure model for particle-based LES that is more accurate and generalizable than current state-of-the-art models. The immediate outcome will be the publication and validation of a novel, GNN-based closure model for particle-based LES, with significant impact potential for enabling higher-fidelity simulations in engineering and science.

### B. Project 2: Interpretability, Generalization, and Verification

**Research Question:** As machine learning models become more integrated into scientific discovery, their "black box" nature presents a critical barrier to adoption in high-stakes applications. My career has spanned the worlds of visual plausibility and numerical accuracy, making me keenly aware that a correct-looking result is not the same as a physically valid one. How can we move beyond simple validation and develop a theoretical framework to interpret what learned models for physical systems are actually learning, and thereby provide guarantees on their generalization and robustness?

**Methodology:** This project will use the Mori-Zwanzig (MZ) formalism from statistical mechanics as a tool for interpreting learned physical models. The MZ formalism decomposes a system's dynamics into a Markovian part (what is known and resolved), a memory kernel (the unresolved, non-local history effects), and a noise term. In a hybrid simulation, the numerical solver can represent the Markovian component, and a well-trained neural network can realize the memory kernel. This combination will allow for more verifiable and theoretically grounded applications of machine learning for physics.

**Relationship to Project 1 & Long-Term Vision:** In short, Project 1 builds the tool; Project 2 provides the theory to trust it. Insights from this interpretability analysis will directly inform the development of more robust, physically-constrained architectures, creating a mutually beneficial relationship that will give the projects room to grow and build on each other.

## IV. Long-Term Impact

My ultimate research goal is to shift how we use physical simulations: moving from tools of passive analysis to active components for design, optimization, and real-time control. The primary barrier to this future is the fundamental trade-off between the speed of data-driven models and the verifiable rigor of numerical methods. My research is designed to resolve this tension directly. By creating hybrid frameworks where learned components are constrained and stabilized by a backbone of proven numerical solvers. The long-term impact of this work will be a new class of trusted, physically-grounded machine learning systems that can accelerate the development of everything from more energy-efficient vehicles to next-generation clean energy systems.

## Possible research directions

This is just a broad overview and rough in its presentation, if you'd like to know more about one of these points, feel free to reach out.

Possible research topics beyond the two and potential for international collaboration:

- Detection of shocks in compressible SPH using learned approaches based on differentiable physics to avoid heuristic viscosity switches, e.g., by collaborations with researchers in astrophysics 
- Scaling the differentiable cases both in number of particles but also to highly non-linear problems, e.g., by collaborations with researchers in non-linear optimization  
- High order (spatial and temporal) correction schemes via hybrid solutions 
- Application of learned surrogates for open boundaries in SPH an interesting application of ML  
- Particle Shifting (ALE schemes) very popular in CFD but often heuristical or computationally excessive. Learned shifting approaches would be a great benefit 
- MZ LES Modelling part of an ongoing discussion with Los Alamos National Lab  
- Offshore wind turbines a very important potential application of SPH, both directly and with surrogates
- Real-time control applications an important application of ML, extending the diffSPH framework to deformable solids would allow for novel and interesting research directions on optimal control for these problems, e.g., using Reinforcement Learning  
- Computer Graphics approaches, such as RayTracing are also used in CFD for SPH, e.g., for laser welding to model the absorption of laser light into the melt, showing existing potential for strong collaborative effects  
- Optimal kernel functions in SPH are a long standing issue, using differentiable physics might be a novel approach to identifying optimal kernel shapes or changing shapes such as done in adaptive sinc kernels that are actively being used by the european EXA-SPH project

Many different countries and fields, significant potential for impact of ML \+ SPH in CFD and beyond. Not a topic that is done in 3 years.