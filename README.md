# Synthetic CTA Template-Fitting Framework for Cluster CR Transport Studies

This notebook implements a **synthetic observation and instrument-facing validation module** for testing whether different cosmic-ray (CR) transport scenarios in galaxy clusters remain distinguishable at the level of realistic CTA observations.

Rather than serving as a separate side project, this work is intended as the **observational interface** of a broader research program on magnetic fields, turbulence, and CR transport in the intracluster/intergalactic medium (ICM/IGM).

## Why this notebook exists

The main scientific motivation is not only to model CR transport in clusters, but also to answer a more practical observational question:

> If different physical transport scenarios produce different CR distributions and gamma-ray emissivities, can those differences still be recognized after instrument response, background, PSF smearing, and likelihood fitting?

This notebook is designed to address exactly that step.

## Role within the larger research pipeline

The broader project follows a multi-scale chain:

**magnetic fields / turbulence / plasma physics**  
→ **CR transport in clusters and the IGM**  
→ **hadronic gamma-ray production**  
→ **projected gamma-ray morphology**  
→ **CTA / ASTRI synthetic observation and likelihood analysis**

This notebook focuses on the **last two stages** of that chain.

It takes physically motivated cluster emission models and translates them into **CTA-observable spatial templates**, then uses **real CTA IRFs and Gammapy likelihood fitting** to test whether competing scenarios are distinguishable at the instrument level.

## What this notebook currently does

At its current stage, the notebook provides a **methodological feasibility framework** built on a simplified cluster setup. It includes:

- simplified cluster modeling with an analytic β-model background
- toy CR transport scenarios, including diffusion-dominated and streaming-dominated cases
- hadronic gamma-ray emissivity construction
- projected 2D surface-brightness maps
- spatial template generation for CTA analysis
- real CTA IRF ingestion through Gammapy
- MapDataset construction and truth injection
- template likelihood fitting with competing transport hypotheses
- exposure scans and distinguishability tests using TS / ΔTS
- a scaffold for Monte Carlo realizations and nuisance tests

In other words, this notebook is not just plotting idealized morphologies. It is already implementing the core synthetic-analysis chain needed to ask whether morphology differences survive realistic CTA observation conditions.

## Scientific purpose

The main question explored here is:

> Can CTA distinguish diffusion-dominated and streaming-dominated CR transport scenarios in clusters using gamma-ray morphology?

More specifically, the notebook is meant to test:

1. what different CR transport scenarios would look like after projection onto the sky,
2. whether those differences survive CTA PSF and background,
3. how much observing time is needed before the scenarios become statistically distinguishable,
4. which cases are physically different but observationally degenerate.

This is the key step that turns **theoretical differences** into **observationally testable differences**.

## Current interpretation

The current notebook should be understood as a **prototype for synthetic observables**, not yet as a final cluster-specific forecast.

At the moment, the inputs are intentionally simplified:

- analytic β-model gas structure
- simplified transport prescriptions
- morphology-first comparison
- simplified emissivity construction

This level is useful because it isolates the logic of the analysis pipeline:

- build templates
- fold through the instrument response
- inject truth
- fit competing models
- quantify detectability and distinguishability

So the present version is best interpreted as a **toy / feasibility-level framework** whose main value is to establish the pipeline and identify promising observable regimes.

## How it connects to the main project

This notebook is meant to act as a **bridge layer** between upstream physical modeling and downstream CTA/ASTRI data analysis.

Its role can be summarized in three steps:

1. **Upstream input**  
   Physically motivated CR distributions or emissivity fields coming from cluster/ICM models, MHD simulations, collisionless-MHD calculations, or CRPropa outputs.

2. **Intermediate conversion**  
   Projection into gamma-ray surface-brightness maps and construction of spatial templates.

3. **Downstream output**  
   CTA/ASTRI IRF folding and Gammapy likelihood analysis to assess detectability and distinguishability.

This is why the notebook should not be described as an independent mini-project. It is better understood as the **observational mapping layer** of the main research program.

## What comes next

The next development stage is to replace the current toy inputs with **physically informed templates**.

### Planned next steps

#### 1. Replace the toy cluster setup with upstream physical outputs

The current analytic β-model can be upgraded by reading in:

- gas density fields from MHD or cosmological simulations
- magnetic-field structure and turbulence information
- CR source proxies or CR distributions from CR transport calculations
- 3D emissivity cubes to be projected into observable maps

#### 2. Move from morphology classification to parameter inference

The current comparison mainly asks whether diffusion and streaming can be distinguished as separate scenarios.

A more advanced version should scan physical parameters such as:

- diffusion coefficient normalization
- energy dependence of transport
- magnetic-field scaling
- injection radius or source history
- cluster mass and environment

This would allow CTA distinguishability to constrain the underlying physical parameter space directly.

#### 3. Extend from CTA-only tests to CTA / ASTRI comparative forecasts

Since the broader research program is framed around both **CTAO** and the **ASTRI Mini-Array**, the pipeline should eventually support comparative forecasts for:

- CTA South
- ASTRI Mini-Array
- different exposure times
- different energy ranges
- different angular resolutions

## Why this matters

Many theoretical studies stop at the level of CR distributions or intrinsic gamma-ray emissivity. However, physical differences do not automatically imply observational differences.

This framework is meant to answer the more useful question:

> Which physical transport scenarios remain distinguishable after realistic instrument response and likelihood analysis?

That makes this notebook valuable not only as a science prototype, but also as a foundation for:

- synthetic observables directly comparable with CTAO/ASTRI sensitivities
- high-throughput parameter-scan pipelines
- future GPU/parallel acceleration of synthetic analysis workloads
- instrument-facing validation of upstream MHD / CR transport models

## Recommended project description

A concise way to describe this repository is:

> This project provides a synthetic CTA template-fitting framework for testing cosmic-ray transport scenarios in galaxy clusters. It translates physically motivated CR/gamma-ray models into CTA-observable spatial templates and uses realistic CTA IRFs with Gammapy likelihood fitting to quantify detectability and distinguishability at the instrument level.

## Short version

This notebook is the **bridge between physics and observation**:

**MHD / CR transport outputs**  
→ **gamma-ray emissivity and projected maps**  
→ **CTA / ASTRI instrument folding**  
→ **template likelihood analysis**  
→ **detectability / distinguishability constraints**

That is its main purpose, and that is how it is intended to connect to the larger research program.
